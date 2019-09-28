---
title: Stratégie de sécurité de WPF - ingénierie de sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: a042f0ae1c7673f7d21b39580db3d373835939cd
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353830"
---
# <a name="wpf-security-strategy---security-engineering"></a>Stratégie de sécurité de WPF - ingénierie de sécurité
Trustworthy Computing (informatique de confiance) est une initiative de Microsoft qui vise à garantir la production de code sécurisé. L’Microsoft Security Development Lifecycle (SDL) est un élément clé de l’initiative Trustworthy Computing initiative. Le SDL est une pratique d’ingénierie qui est utilisée conjointement avec les processus d’ingénierie standard pour faciliter la livraison de code sécurisé. Le SDL se compose de dix phases qui associent les meilleures pratiques à la formalisation, à la mesurabilité et à une structure supplémentaire, notamment :  
  
- analyse de la conception de la sécurité ;  
  
- contrôles de qualité basés sur des outils ;  
  
- test de pénétration ;  
  
- réexamen final de la sécurité ;  
  
- gestion de la sécurité du produit après lancement.  
  
## <a name="wpf-specifics"></a>Spécificités de WPF  
 L’équipe d’ingénierie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] applique et étend le SDL, dont la combinaison comprend les aspects clés suivants :  
  
 [Modélisation des menaces](#threat_modeling)  
  
 [Analyse de la sécurité et outils de modification](#tools)  
  
 [Techniques de test](#techniques)  
  
 [Gestion du code critique](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modélisation des menaces  
 La modélisation des menaces est un composant fondamental de SDL et est utilisée pour profiler un système afin de déterminer les failles de sécurité potentielles. Une fois les failles identifiées, la modélisation des menaces permet aussi de s'assurer que des mesures de prévention appropriées ont été prises.  
  
 D'un point de vue général, la modélisation des menaces comporte les étapes clés suivantes, ici appliquées à l'exemple d'une épicerie :  
  
1. **Identification des ressources** : les ressources d'une épicerie peuvent inclure les employés, un coffre-fort, les caisses et le stock.  
  
2. **Énumération des points d’entrée** : les points d'entrée d'une épicerie peuvent inclure les portes de devant et de derrière, les fenêtres, le quai de chargement et les climatiseurs.  
  
3. **Réflexion sur les attaques possibles à l’encontre des ressources via les points d’entrée** : dans une épicerie, le *coffre-fort* peut être la cible d’une attaque via le point d’entrée que constitue le *climatiseur* ; celui-ci pourrait être démonté et, par le passage ainsi libéré, permettre d’extraire le coffre-fort hors du magasin.  
  
 La modélisation des menaces s'applique à l'échelle de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] et comprend les éléments suivants :  
  
- Comment l'analyseur [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] lit les fichiers, mappe le texte aux classes de modèle objet correspondantes et crée le code réel.  
  
- Comment un handle de fenêtre (hWnd) est créé, envoie des messages et est utilisé pour restituer le contenu d'une fenêtre.  
  
- Comment la liaison de données obtient les ressources et interagit avec le système.  
  
 Ces modèles de menace sont importants pour identifier les spécifications de conception de sécurité et les mesures de prévention pendant le processus de développement.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Analyse de la source et outils de modification  
 Outre les éléments manuels de révision du code de sécurité de SDL, l’équipe [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] utilise plusieurs outils pour l’analyse de la source et les modifications associées pour réduire les vulnérabilités de sécurité. Une large gamme d’outils sources est utilisée et comprend les éléments suivants :  
  
- **FxCop**: Recherche des problèmes de sécurité courants dans le code managé, allant des règles d’héritage à l’utilisation de la sécurité d’accès du code à la manière d’interagir en toute sécurité avec du code non managé. Consultez la page [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Préfixe/prérapide**: Recherche les failles de sécurité et les problèmes de sécurité courants dans le code non managé, tels que les dépassements de mémoire tampon, les problèmes de chaîne de format et la vérification des erreurs.  
  
- **API interdites**: Recherche du code source pour identifier l’utilisation accidentelle de fonctions connues pour provoquer des problèmes de sécurité, tels que `strcpy`. Une fois identifiés, ces fonctions sont remplacées par des alternatives plus sécurisées.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniques de test  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] utilise plusieurs techniques de test de sécurité, à savoir :  
  
- **Test WhiteBox**: Les testeurs affichent le code source, puis génèrent des tests d’exploitation.
  
- **Tests Blackbox**: Les testeurs essaient de trouver des failles de sécurité en examinant l’API et les fonctionnalités, puis essaient d’attaquer le produit.  
  
- **Régression des problèmes de sécurité à partir d’autres produits**: Le cas échéant, les problèmes de sécurité provenant de produits connexes sont testés. Par exemple, les variantes appropriées d’environ 60 problèmes de sécurité pour Internet Explorer ont été identifiées et essayées pour leur applicabilité à [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
- **Tests de pénétration basés sur des outils via le fuzzing de fichiers**: Le fuzzing de fichier est l’exploitation de la plage d’entrée d’un lecteur de fichier par le biais de diverses entrées. Par exemple, dans [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], cette technique est employée pour rechercher des défaillances dans le code de décodage d'image.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Gestion du code critique  
 Par [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] crée un bac à sable (sandbox) de sécurité à l’aide de .NET Framework prise en charge du marquage et du suivi du code critique de sécurité qui élève les privilèges (consultez **méthodologie critique de sécurité** dans [stratégie de sécurité de WPF-sécurité](wpf-security-strategy-platform-security.md)de la plateforme). Compte tenu des hautes exigences de qualité en matière de sécurité sur le code critique de sécurité, un tel code bénéficie d'un niveau de contrôle supplémentaire sur le plan de la gestion de la source et de l'audit de sécurité. Environ 5 à 10 % de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] est constitué de code critique de sécurité, qui est examiné par une équipe de révision dédiée. Le processus de code source et d’archivage est géré par le suivi du code critique de sécurité et le mappage de chaque entité critique (c’est-à-dire, une méthode qui contient le code critique) à son état de validation. L'état de validation s'accompagne des noms d'un ou plusieurs réviseurs. Chaque build quotidienne de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compare le code critique à celui des versions précédentes pour vérifier la présence éventuelle de modifications non approuvées. Si un ingénieur modifie du code critique sans l'approbation de l'équipe de révision, celui-ci est identifié et corrigé immédiatement. Ce processus permet d'appliquer et de maintenir un niveau particulièrement élevé de surveillance sur le code du bac à sable (sandbox) [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité](security-wpf.md)
- [Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md)
- [Stratégie de sécurité de WPF - sécurité de la plateforme](wpf-security-strategy-platform-security.md)
- [Informatique fiable](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Sécurité dans .NET](../../standard/security/index.md)
