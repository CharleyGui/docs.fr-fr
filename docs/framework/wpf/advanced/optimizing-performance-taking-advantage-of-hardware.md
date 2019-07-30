---
title: 'Optimisation des performances: Tirer parti du matériel'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 7acf5a3f48ac4987037873c63111d988ec3a4979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629650"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimisation des performances: Tirer parti du matériel
L’architecture interne de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dispose de deux pipelines de rendu, matériels et logiciels. Cette rubrique fournit des informations sur ces pipelines de rendu pour vous aider à prendre des décisions sur les optimisations de performances de vos applications.  
  
## <a name="hardware-rendering-pipeline"></a>Pipeline de rendu matériel  
 L’un des facteurs les plus importants pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déterminer les performances est qu’il s’agit d’un rendu lié: plus il y a de pixels à afficher, plus le coût des performances est élevé. Toutefois, plus le rendu peut être déchargé dans [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], plus les performances que vous pouvez obtenir sont avantageuses. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu matériel des applications tire pleinement parti des fonctionnalités de Microsoft DirectX sur du matériel qui prend en charge Microsoft DirectX version 7,0 au minimum. D’autres optimisations peuvent être obtenues par le matériel qui prend en charge les fonctionnalités de Microsoft DirectX version 7,0 et PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Pipeline de rendu logiciel  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu logiciel est entièrement lié à l’UC. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tire parti des jeux d’instructions SSE et SSE2 dans le processeur pour implémenter un rastériseur logiciel optimisé et complet. Le recours au logiciel est transparent à chaque fois que la fonctionnalité de l’application ne peut pas être rendue à l’aide du pipeline de rendu matériel.  
  
 Le plus grand problème de performances que vous pouvez rencontrer lors du rendu en mode logiciel est lié au taux de remplissage, qui est défini comme le nombre de pixels que vous rendez. Si vous vous souciez des performances en mode de rendu logiciel, essayez de réduire le nombre de rafraîchissements d’un pixel. Par exemple, si vous avez une application avec un arrière-plan bleu, qui affiche ensuite une image légèrement transparente sur celle-ci, vous allez restituer tous les pixels de l’application à deux reprises. Par conséquent, le rendu de l’application avec l’image prendra deux fois plus de temps que si vous aviez uniquement l’arrière-plan bleu.  
  
### <a name="graphics-rendering-tiers"></a>Couches de rendu graphiques  
 Il peut être très difficile de prédire la configuration matérielle sur laquelle votre application s’exécutera. Toutefois, vous pouvez envisager une conception qui permet à votre application de basculer en toute transparence les fonctionnalités lorsqu’elles s’exécutent sur un autre matériel, afin de tirer pleinement parti de chaque configuration matérielle.  
  
 Pour ce faire, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des fonctionnalités permettant de déterminer la capacité graphique d’un système au moment de l’exécution. La fonctionnalité graphique est déterminée en classant la carte vidéo comme l’un des trois niveaux de capacité de rendu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]expose une API qui permet à une application d’interroger le niveau de fonctionnalité de rendu. Votre application peut ensuite prendre des chemins de code différents au moment de l’exécution en fonction de la couche de rendu prise en charge par le matériel.  
  
 Les fonctionnalités du matériel graphique qui ont le plus d’impact sur les niveaux de la couche de rendu sont les suivantes :  
  
- **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
- **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel. En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque image de l’affichage.  
  
- **Nuanceur de sommets** Un nuanceur de sommets est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de sommet de l’objet.  
  
- **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d’appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D. Le degré de prise en charge de la multitexture est déterminé par le nombre d’unités de multitexture sur le matériel graphique.  
  
 Le nuanceur de pixels, le nuanceur de sommets et les fonctionnalités de multitexture sont utilisés pour définir des niveaux de version DirectX spécifiques, qui, à leur tour, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sont utilisés pour définir les différents niveaux de rendu dans.  
  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d’une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
- **Couche de rendu 0** Aucune accélération matérielle graphique. Le niveau de version de DirectX est inférieur à la version 7,0.  
  
- **Niveau de rendu 1** Accélération matérielle graphique partielle. Le niveau de version de DirectX est supérieur ou égal à la version 7,0 **, et inférieur** à la version 9,0.  
  
- **Couche de rendu 2** La plupart des fonctionnalités graphiques utilisent l’accélération matérielle graphique. Le niveau de version de DirectX est supérieur ou égal à la version 9,0.  
  
 Pour plus d’informations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur les niveaux de rendu, consultez [couches de rendu graphiques](graphics-rendering-tiers.md).  
  
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
