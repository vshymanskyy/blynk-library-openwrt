include $(TOPDIR)/rules.mk

PKG_NAME:=python-blynk-library
PKG_VERSION:=0.1.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Volodymyr Shymanskyy
PKG_LICENSE:=MIT

PKG_SOURCE:=blynk-library-python-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/40/8d/ca3721c7f2a8c4305a1dbbefc4d22b3221c28042e94bb4a2aa91169b4943
PKG_MD5SUM:=3fa1bc0b98d270a95876d772c6906239

PKG_BUILD_DIR:=$(BUILD_DIR)/blynk-library-python-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python python-setuptools

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-blynk-library
	SUBMENU:=Python
	SECTION:=lang
	CATEGORY:=Languages
	TITLE:=Blynk client for Python
	URL:=https://github.com/vshymanskyy/blynk-library-python
	DEPENDS:=+python-light +python-codecs
endef

define Package/python-blynk-library/description
 Blynk is a platform with iOS and Android apps to control Arduino,
 Raspberry Pi and the likes over the Internet.
 You can easily build graphic interfaces for all your projects
 by simply dragging and dropping widgets.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="$(PKG_INSTALL_DIR)/usr")
endef

define Package/python-blynk-library/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-blynk-library))
