#
# Copyright (C) 2014-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libpd
PKG_VERSION:=0.11.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:libpd/libpd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_MIRROR_HASH:=95669bb419d1bd5018dccebd9e09d62b53132da7d7dac20bc85a8b0399180026
PKG_MAINTAINER:=

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE.txt

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libpd
  SECTION:=sound
  CATEGORY:=Sound
  DEPENDS:=
  TITLE:=LibPD
endef

define Package/libpd/description
  LibPD
endef

MAKE_FLAGS += \
  OPT_CFLAGS="$(TARGET_CFLAGS)" \
  prefix="/usr" \

define Package/libpd/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpd.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpd))
