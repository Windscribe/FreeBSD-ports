PORTNAME=	deforaos-browser
PORTVERSION=	0.5.5
PORTREVISION=	1
CATEGORIES=	x11-fm
MASTER_SITES=	https://ftp.defora.org/pub/DeforaOS/Apps/Desktop/src/Browser/
DISTNAME=	Browser-${PORTVERSION}

MAINTAINER=	khorben@defora.org
COMMENT=	DeforaOS desktop file browser
WWW=		https://www.defora.org/

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libSystem.so:devel/deforaos-libsystem \
		libDesktop.so:x11/deforaos-libdesktop \
		libharfbuzz.so:print/harfbuzz \
		libXrandr.so:x11/libXrandr

USES=		gnome pkgconfig xorg desktop-file-utils

OPTIONS_DEFINE=	DOCS NLS
OPTIONS_SUB=	yes
NLS_USES=		gettext
DOCS_BUILD_DEPENDS=	xsltproc:textproc/libxslt \
    ${LOCALBASE}/share/xsl/docbook/manpages/docbook.xsl:textproc/docbook-xsl

USE_GNOME=	gtk30 cairo gdkpixbuf2
USE_XORG=	x11
USE_LDCONFIG=	yes
MAKE_ARGS+=	PREFIX=${PREFIX}
MAKE_ENV+=	MANDIR=${STAGEDIR}${MANPREFIX}/man

CONFLICTS_INSTALL=	schilyutils silo # bin/browser bin/copy
post-patch:
	${REINPLACE_CMD} -e 's|/lib/|/libdata/|g' \
		${WRKSRC}/data/pkgconfig.sh

post-patch-DOCS-off:
	${REINPLACE_CMD} -e '/^SUBDIRS/ s|doc||' ${WRKSRC}/Makefile

post-patch-NLS-off:
	${REINPLACE_CMD} 's|include po src|include src|' \
		${WRKSRC}/Makefile

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/* \
		${STAGEDIR}${PREFIX}/lib/Desktop/widget/browser.so \
		${STAGEDIR}${PREFIX}/lib/Browser/plugins/* \
		${STAGEDIR}${PREFIX}/lib/libBrowser.so.0.0

.include <bsd.port.mk>
