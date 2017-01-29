#
# Copyright (C) 2017 Venelin Efremov <vefremov@iqury.us>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dbuswrapper
PKG_VERSION=0.1.2
PKG_RELEASE:=1
PKG_MAINTAINER:=Venelin Efremov <vefremov@iqury.us>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=git@bitbucket.org:ghent360/dbuswrapper.git
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=dc7e992a2bfd28bbf496acb2ec5cc652955948b4
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

define Package/dbuswrapper
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libstdcpp +libpthread +gflags +glog +dbus
  TITLE:=C++ wrapper library for DBUS.
  URL:=https://bitbucket.org/ghent360/dbuswrapper
endef

define Package/dbuswrapper/description
  C++ wrapper library for DBUS
endef

define Package/dbuswrapper/install
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
	$(INSTALL_DIR) $(1)/usr/include/dbus-wrapper
	$(CP) $(PKG_INSTALL_DIR)/usr/include/dbus-wrapper $(1)/usr/include/dbus-wrapper
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/*.pc \
		$(1)/usr/lib/pkgconfig
endef

$(eval $(call BuildPackage,dbuswrapper))
