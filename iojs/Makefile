include $(TOPDIR)/rules.mk

PKG_NAME:=iojs
PKG_VERSION:=v3.3.0
PKG_RELEASE:=1

PKG_SOURCE:=iojs-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://iojs.org/dist/latest/
PKG_SHA256SUM:=e84a649858e6f5c1458c0d5d7bf1952f78e93a26ea6bc519222e92e43e2fadde

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/iojs
  DEPENDS:=+libpthread +librt +libstdcpp +libopenssl +zlib
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=io.js is an npm compatible platform originally based on Node.js.
  URL:=https://iojs.org
endef

define Package/iojs/description
io.js is an npm compatible platform originally based on Node.js.
endef

ifeq ($(ARCH),arm)
  ifeq ($(HAS_FPU),y)
    NODEJS_ARM_FP=soft
  else
    NODEJS_ARM_FP=softfp
  endif
endif

CONFIGURE_ARGS = \
           --prefix=/usr \
           --dest-cpu=$(ARCH) \
           --dest-os=linux \
           --without-snapshot \
           --without-dtrace  \
           --shared-openssl \
           --shared-zlib \
           $(if $(NODEJS_ARM_FP),--with-arm-float-abi=$(NODEJS_ARM_FP))

define Build/Configure
  $(call Build/Configure/Default)
endef

define Build/Compile
  $(call Build/Compile/Default)
endef

define Package/iojs/install
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) DESTDIR="$(1)" install
endef

$(eval $(call BuildPackage,iojs))
