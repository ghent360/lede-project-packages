include $(TOPDIR)/rules.mk

PKG_NAME:=octoprint
PKG_VERSION:=1.3.9
PKG_RELEASE:=1.3.9
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/foosel/OctoPrint.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=d3871e34873aa55476a8173859239a1a490fa279
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/

#PKG_BUILD_DEPENDS:=python-setuptools 

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/octoprint
    SECTION:=lang-python
    CATEGORY:=Languages
    SUBMENU:=Python
    TITLE:=OctoPrint
    URL:=https://pypi.python.org/pypi/idna
    DEPENDS:=+python
endef

define Package/OctoPrint/description
    The snappy web interface for your 3D printer.
    Created & maintained by Gina Häußge
endef

define Build/Compile
    $(call Build/Compile/PyMod,., \
        install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
    )
endef

define Build/InstallDev
    $(INSTALL_DIR) $(STAGING_DIR)$(PYTHON_PKG_DIR)
    $(CP) \
        $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
        $(STAGING_DIR)$(PYTHON_PKG_DIR)/
    [ ! -e $(PKG_INSTALL_DIR)/usr/include ] || $(CP) \
        $(PKG_INSTALL_DIR)/usr/include/* \
        $(STAGING_DIR)/usr/include/
endef

define Package/OctoPrint/install
    $(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
    $(CP) \
        $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
        $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,OctoPrint))
