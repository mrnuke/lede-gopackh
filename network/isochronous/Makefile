#
# How to build isochronous as a LEDE package 101
#

include $(TOPDIR)/rules.mk

PKG_NAME:=isochronous
PKG_SOURCE_VERSION:=bf2ec7434e3446383f1f3287b9d4403b9b0a6259
PKG_VERSION:=$(PKG_SOURCE_VERSION)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/dtaht/isochronous.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)


include $(INCLUDE_DIR)/package.mk

define Package/isochronous
  SECTION:=gopackh
  CATEGORY:=GoPackH
  TITLE:=Three tools to test bursty and isochronous network behavior.
  URL:=https://github.com/dtaht/isochronous
endef

define Package/isochronous/description
  This is a place to stash three tools testing bursty and isochronous behavior
  as they evolve.
endef

define Package/isochronous/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/isoping $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/isostream $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/udpstress $(1)/usr/bin
endef

$(eval $(call BuildPackage,isochronous))
