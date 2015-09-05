#
# Copyright (C) 2007-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=senmqd
PKG_VERSION:=0.0.0
PKG_REV:=d0157bb19dbc7c364b6f6679ce9a978fd6099d75
PKG_RELEASE:=1
PKG_LICENSE:=GPL-3.0+
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE:=senmqd-$(PKG_REV).tar.bz2
PKG_SOURCE_SUBDIR:=senmqd-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/Mic92/senmqd/
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/senmqd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Gpio Inputs distributed subscribable via zmq
  URL:=https://github.com/tuxcodejohn/senmqd
  MAINTAINER:=Joerg Thalheim <joerg@higgsboson.tk>
  DEPENDS:=+libzmq +libstdcpp
endef

define Package/senmqd/description
   Gpio Inputs distributed subscribable via zmq
endef

define Package/senmqd/install
	@echo $(INSTALL_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

$(eval $(call BuildPackage,senmqd))

