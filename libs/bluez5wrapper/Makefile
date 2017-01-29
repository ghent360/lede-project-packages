#
# Copyright (C) 2017 Venelin Efremov <vefremov@iqury.us>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluez5wrapper
PKG_VERSION=0.1.2
PKG_RELEASE:=1
PKG_MAINTAINER:=Venelin Efremov <vefremov@iqury.us>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=git@bitbucket.org:ghent360/blues5wrapper.git
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=de8945acbb7f70d7c076c67acad8058d266c3e44
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_MD5SUM:=2416b7c49b37838eefa265f766af6f84dec82fa7cfbdbe25868834d1717b4054

include $(INCLUDE_DIR)/package.mk

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

define Package/bluez5wrapper
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libstdcpp +libpthread +gflags +glog +dbus +dbuswrapper
  TITLE:=C++ wrapper library for Bluez 5.
  URL:=https://bitbucket.org/ghent360/blues5wrapper
endef

define Package/bluez5wrapper/description
  C++ wrapper library for Bluez 5
endef

define Package/bluez5wrapper/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
endef

define Build/Configure
	(cd $(PKG_BUILD_DIR); rm -rf config.{cache,status}; \
		autoreconf -vif \
	);
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/bluez5-cxx
	$(CP) $(PKG_INSTALL_DIR)/usr/include/bluez5-cxx/* $(1)/usr/include/bluez5-cxx
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/*.pc \
		$(1)/usr/lib/pkgconfig
endef

$(eval $(call BuildPackage,bluez5wrapper))
