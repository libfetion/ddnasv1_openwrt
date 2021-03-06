#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gst-plugins-bad
PKG_VERSION:=0.10.19
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://gstreamer.freedesktop.org/src/gst-plugins-bad/
PKG_MD5SUM:=368f72e2a1c7a6e8fe60394e4315259b

PKG_BUILD_DEPENDS:= gstreamer gst-plugins-base liboil

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/gstreamer/Default
  CATEGORY:=Multimedia
  SECTION:=multimedia
  TITLE:=GStreamer
  URL:=http://gstreamer.freedesktop.org/
endef

define Package/gstreamer/description/Default
 GStreamer open source multimedia framework
endef


define Package/gst-plugins-bad
$(call Package/gstreamer/Default)
  TITLE+= plugins collection (bad)
  DEPENDS+= $(GST_DEPENDS)
endef

define Package/gts-plugins-bad/description
$(call Package/gstreamer/description/Default)
 .
 This meta package contains only dependencies to the other plugins from
 the bad plugins collection.
endef


GST_VERSION:=0.10

CONFIGURE_ARGS += \
	--disable-debug \
	--disable-examples \
	--disable-nls	\
	\
	--disable-directsound \
	--disable-directdraw \
	--disable-osx_video \
	--disable-quicktime \
	--disable-vcd \
	--disable-alsa \
	--disable-assrender \
	--disable-amrwb \
	--disable-apexsink \
	--disable-bz2 \
	--disable-cdaudio \
	--disable-celt \
	--disable-cog \
	--disable-dc1394 \
	--disable-directfb \
	--disable-dirac \
	--disable-dts \
	--disable-divx \
	--disable-resindvd \
	--disable-metadata \
	--disable-faac \
	--disable-faad \
	--disable-fbdev \
	--disable-flite \
	--disable-gsm \
	--disable-jack \
	--disable-jp2k \
	--disable-kate \
	--disable-ladspa \
	--disable-lv2 \
	--disable-modplug \
	--disable-mimic \
	--disable-mpeg2enc \
	--disable-mplex \
	--disable-musepack \
	--disable-musicbrainz \
	--disable-mythtv \
	--disable-nas \
	--disable-neon \
	--disable-ofa \
	--disable-rsvg \
	--disable-timidity \
	--disable-wildmidi \
	--disable-sdl \
	--disable-sdltest \
	--disable-sndfile \
	--disable-soundtouch \
	--disable-spc \
	--disable-gme \
	--disable-swfdec \
	--disable-theoradec \
	--disable-xvid \
	--disable-dvb \
	--disable-wininet \
	--disable-acm \
	--disable-vdpau \
	--disable-schro \
	--disable-zbar \
	--disable-vp8 \
	--disable-librfb \
	\
	--without-libiconv-prefix \
	--without-libintl-prefix \
	--without-x \

EXTRA_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \


define Package/gst-plugins-ugly/install
	/bin/true
endef


# 1: short name
# 2: description
# 3: dependencies on other gstreamer libraries (short name)
# 4: dependencies on other gstreamer plugins (short name)
# 5: dependencies on other packages
define GstBuildPlugin

  GST_DEPENDS += +gst-mod-$(1)

  define Package/gst-mod-$(1)
    $(call Package/gstreamer/Default)
    TITLE+= $(2) plugin (bad)
    DEPENDS+= +libgstreamer $$(foreach p,$(3),+libgst$$(p)) $$(foreach p,$(4),+gst-mod-$$(p)) $(5)
  endef

  define Package/gst-mod-$(1)/description
   $(call Package/gstreamer/description/Default)
   .
   This package contains the GStreamer $(2) plugin.
  endef

  define Package/gst-mod-$(1)/install
	$(INSTALL_DIR) $$(1)/usr/lib/gstreamer-$(GST_VERSION)
	( cd $(PKG_INSTALL_DIR); $(CP) \
		./usr/lib/gstreamer-$(GST_VERSION)/libgst$(1).so* \
		$$(1)/usr/lib/gstreamer-$(GST_VERSION)/ \
	)
  endef

  $$(eval $$(call BuildPackage,gst-mod-$(1)))
endef

$(eval $(call GstBuildPlugin,adpcmdec,adpcm decoding support,,,))
$(eval $(call GstBuildPlugin,adpcmenc,adpcm encoding support,,,))
$(eval $(call GstBuildPlugin,aiff,aiff support,,,))
$(eval $(call GstBuildPlugin,asfmux,asf muxing support,,,))
$(eval $(call GstBuildPlugin,audioparsersbad,audioparsers support,,,))
$(eval $(call GstBuildPlugin,autoconvert,autoconvert support,,,))
$(eval $(call GstBuildPlugin,camerabin,camerabin support,,,))
$(eval $(call GstBuildPlugin,legacyresample,legacyresample support,,,))
$(eval $(call GstBuildPlugin,bayer,bayer support,,,))
$(eval $(call GstBuildPlugin,cdxaparse,cdxaparse support,,,))
$(eval $(call GstBuildPlugin,dataurisrc,dataurisrc support,,,))
$(eval $(call GstBuildPlugin,dccp,dccp support,,,))
$(eval $(call GstBuildPlugin,debugutilsbad,debugutils support,,,))
$(eval $(call GstBuildPlugin,dtmf,dtmf support,,,))
$(eval $(call GstBuildPlugin,dvdspu,dvdspu support,,,))
$(eval $(call GstBuildPlugin,festival,festival support,,,))
$(eval $(call GstBuildPlugin,freeze,freeze support,,,))
$(eval $(call GstBuildPlugin,frei0r,frei0r support,,,))
$(eval $(call GstBuildPlugin,h264parse,h264parse support,,,))
$(eval $(call GstBuildPlugin,hdvparse,hdvparse support,,,))
$(eval $(call GstBuildPlugin,id3tag,id3tag support,,,))
$(eval $(call GstBuildPlugin,invtelecine,invtelecine support,,,))
$(eval $(call GstBuildPlugin,jpegformat,jpegformat support,,,))
#$(eval $(call GstBuildPlugin,librfbsrc,librfb support,,,))
$(eval $(call GstBuildPlugin,liveadder,liveadder support,,,))
$(eval $(call GstBuildPlugin,mpegdemux,mpegdemux support,,,))
$(eval $(call GstBuildPlugin,mpegtsmux,mpegtsmux support,,,))
$(eval $(call GstBuildPlugin,mpegpsmux,mpegpsmux support,,,))
$(eval $(call GstBuildPlugin,mpeg4videoparse,mpeg4videoparse support,,,))
$(eval $(call GstBuildPlugin,mpegvideoparse,mpegvideoparse support,,,))
$(eval $(call GstBuildPlugin,mve,mve support,,,))
$(eval $(call GstBuildPlugin,mxf,mxf support,,,))
$(eval $(call GstBuildPlugin,nsf,nsf support,,,))
$(eval $(call GstBuildPlugin,nuvdemux,nuvdemux support,,,))
$(eval $(call GstBuildPlugin,pcapparse,pcapparse support,,,))
$(eval $(call GstBuildPlugin,pnm,pnm support,,,))
$(eval $(call GstBuildPlugin,qtmux,qtmux support,,,))
$(eval $(call GstBuildPlugin,rawparse,rawparse support,,,))
$(eval $(call GstBuildPlugin,rtpmux,rtpmux support,,,))
#$(eval $(call GstBuildPlugin,rfbsrc,rfb support,,,))
$(eval $(call GstBuildPlugin,scaletempoplugin,scaletempo support,,,))
$(eval $(call GstBuildPlugin,sdpelem,sdp support,,,))
$(eval $(call GstBuildPlugin,segmentclip,segmentclip support,,,))
$(eval $(call GstBuildPlugin,selector,selector support,,,))
$(eval $(call GstBuildPlugin,siren,siren support,,,))
$(eval $(call GstBuildPlugin,speed,speed support,,,))
$(eval $(call GstBuildPlugin,subenc,subenc support,,,))
$(eval $(call GstBuildPlugin,stereo,stereo support,,,))
$(eval $(call GstBuildPlugin,tta,tta support,,,))
$(eval $(call GstBuildPlugin,valve,valve support,,,))
$(eval $(call GstBuildPlugin,videomeasure,videomeasure support,,,))
$(eval $(call GstBuildPlugin,videosignal,videosignal support,,,))
$(eval $(call GstBuildPlugin,vmnc,vmnc support,,,))
$(eval $(call GstBuildPlugin,mms,mms support,,,+libmms))

$(eval $(call BuildPackage,gst-plugins-bad))
