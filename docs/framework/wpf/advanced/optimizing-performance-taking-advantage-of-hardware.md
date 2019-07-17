---
title: 'Optimisation des performances : Tirer parti du matériel'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 13812fa5429bbe33341e51e4b3be14fbbcb361cb
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238449"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimisation des performances : Tirer parti du matériel
L’architecture interne de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a deux pipelines de rendu matériel et logiciel. Cette rubrique fournit des informations sur ces pipelines de rendu pour vous aider à prendre des décisions sur les optimisations des performances de vos applications.  
  
## <a name="hardware-rendering-pipeline"></a>Pipeline de rendu matériel  
 Un des facteurs plus importants dans la détermination [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] performances sont qu’il s’agit de limite de rendu — les pixels plus avoir à restituer, plus l’impact sur les performances. Toutefois, plus de rendu qui peuvent être déchargées sur le [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], les gains de performance plus que vous pouvez obtenir. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu matériel application tire pleinement parti de [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] fonctionnalités sur du matériel qui prend en charge un minimum de [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0. Des optimisations supplémentaires peuvent être obtenues par matériel qui prend en charge [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0 et les fonctionnalités PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Pipeline de rendu logiciel  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu logiciel est entièrement lié au processeur. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tire parti de l’instruction SSE et SSE2 définit dans le processeur pour implémenter un rastériseur logiciel optimisé et riche en fonctionnalités. Le recours au logiciel est transparent chaque fois que fonctionnalités de l’application ne peut pas être restituée à l’aide du pipeline de rendu matériel.  
  
 Le plus gros problème de performances vous rencontrerez lors de rendu en mode logiciel est lié au taux de remplissage, qui est défini comme le nombre de pixels rendus. Si vous êtes inquiet de performances en mode de rendu logiciel, essayez de réduire le nombre de fois où qu'un pixel est redessiné. Par exemple, si vous disposez d’une application avec un arrière-plan bleu, qui restitue ensuite une image légèrement transparente sur celui-ci, vous affichera tous les pixels dans l’application à deux reprises. Par conséquent, il prendra à deux reprises tant pour le rendu de l’application avec l’image que si vous aviez seulement l’arrière-plan est bleu.  
  
### <a name="graphics-rendering-tiers"></a>Couches de rendu graphiques  
 Il peut être très difficile de prévoir la configuration matérielle qui fonctionnent sur votre application. Toutefois, vous souhaiterez peut-être envisager une conception qui permet à votre application basculer en toute transparence fonctionnalités lors de l’exécution sur un matériel différent, afin qu’elle puisse tirer pleinement parti de chaque configuration matérielle.  
  
 Pour y parvenir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des fonctionnalités permettant de déterminer la capacité de graphique d’un système lors de l’exécution. Des fonctionnalités graphiques sont déterminée en classant la carte vidéo comme l’un des trois couches de rendu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expose une API qui permet à une application interroger le niveau de fonctionnalité de rendu. Votre application peut alors prendre des chemins de code différents au moment de l’exécution en fonction de la couche de rendu pris en charge par le matériel.  
  
 Les fonctionnalités du matériel graphique qui ont le plus d’impact sur les niveaux de la couche de rendu sont les suivantes :  
  
- **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
- **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel. En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque image de l’affichage.  
  
- **Nuanceur de sommets** Un nuanceur de sommets est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de sommet de l’objet.  
  
- **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d’appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D. Le degré de prise en charge de la multitexture est déterminé par le nombre d’unités de multitexture sur le matériel graphique.  
  
 Nuanceur de pixels, nuanceur de sommets, les fonctionnalités de multitexture servent à définir spécifique [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] les niveaux de version, qui, à son tour, sont utilisés pour définir les différentes couches de rendu dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d’une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
- **Couche de rendu 0** Aucune accélération matérielle graphique. Le [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] au niveau de version est inférieure à la version 7.0.  
  
- **Couche de rendu 1** l’accélération matérielle graphique partielle. Le [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] au niveau de version est supérieure ou égale à la version 7.0, et **moindre** à la version 9.0.  
  
- **Couche de rendu 2** La plupart des fonctionnalités graphiques utilisent l’accélération matérielle graphique. Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 9.0.  
  
 Pour plus d’informations sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] couches de rendu, consultez [couches de rendu graphiques](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
