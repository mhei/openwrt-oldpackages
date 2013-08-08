#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=opensunny
PKG_VERSION:=2013-08-04
PKG_RELEASE=$(PKG_SOURCE_VERSION)-1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:simonswine/opensunny.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=971208a8393050c93b2b4e414483137571bf820d
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.bz2

include $(INCLUDE_DIR)/package.mk

define Package/opensunny
  SECTION:=utils
  CATEGORY:=Utilities
  URL:=https://github.com/simonswine/opensunny
  TITLE:=Linux tool to query SMA inverters via bluetooth
  DEPENDS:=+bluez-libs
endef

define Package/opensunny/description
  opensunny is a very project in a very early stage. The goal is to
  create a free and open solution to query SMA's bluetooth enabled
  inverters e.g. SMA Sunny Boys.
endef

define Build/Configure
endef

define Package/opensunny/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/opensunny $(1)/usr/bin/
endef

$(eval $(call BuildPackage,opensunny))
