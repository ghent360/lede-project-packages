#
# Copyright (C) 2017 Venelin Efremov <vefremov@iqury.us>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gflags
PKG_VERSION=2.2.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Venelin Efremov <vefremov@iqury.us>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=COPYING.txt

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/gflags/gflags/
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=30dbc81fb5ffdc98ea9b14b1918bfe4e8779b26e
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_MD5SUM:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += \
    -DBUILD_SHARED_LIBS:BOOL=ON \
    -DBUILD_STATIC_LIBS:BOOL=OFF\

define Package/gflags
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libstdcpp
  TITLE:=Google gflags library
  URL:=https://github.com/gflags/gflags
endef

define Package/gflags/description
  Google gflags library
endef

define Package/gflags/install	
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/lib/libgflags.so* $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/gflags
	$(CP) $(PKG_BUILD_DIR)/include/gflags/* $(1)/usr/include/gflags
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/lib/libgflags.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/lib/libgflags_nothreads.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/cmake/gflags
	$(CP) $(PKG_BUILD_DIR)/gflags*.cmake $(1)/usr/lib/cmake/gflags/
endef

$(eval $(call BuildPackage,gflags))
