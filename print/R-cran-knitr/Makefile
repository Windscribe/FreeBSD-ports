PORTNAME=	knitr
PORTVERSION=	1.45
CATEGORIES=	print
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	uzsolt@uzsolt.hu
COMMENT=	General-Purpose Package for Dynamic Report Generation in R
WWW=		https://cran.r-project.org/web/packages/knitr/

LICENSE=	GPLv2+

CRAN_DEPENDS=	R-cran-evaluate>=0.15:devel/R-cran-evaluate \
		R-cran-highr>0:textproc/R-cran-highr \
		R-cran-yaml>=2.1.19:textproc/R-cran-yaml \
		R-cran-xfun>=0.34:misc/R-cran-xfun
BUILD_DEPENDS=	${CRAN_DEPENDS}
RUN_DEPENDS=	${CRAN_DEPENDS}

USES=		cran:auto-plist

.include <bsd.port.mk>
