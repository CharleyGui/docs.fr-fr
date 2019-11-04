---
title: "Optimisation des performances : ressources d'application"
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 59b124c28ade0a6c5119b651ff935d460bf4516d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458561"
---
# <a name="optimizing-performance-application-resources"></a>Optimisation des performances : ressources d'application
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de partager des ressources d’application afin de pouvoir prendre en charge une apparence ou un comportement cohérent sur des éléments de type similaire. Cette rubrique fournit quelques recommandations dans ce domaine qui peuvent vous aider à améliorer les performances de vos applications.  
  
 Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="sharing-resources"></a>Partager des ressources  
 Si votre application utilise des contrôles personnalisés et définit des ressources dans un <xref:System.Windows.ResourceDictionary> (ou un nœud de ressources XAML), il est recommandé de définir les ressources au niveau de l’objet <xref:System.Windows.Application> ou <xref:System.Windows.Window>, ou de les définir dans le thème par défaut pour les contrôles personnalisés. La définition de ressources dans le <xref:System.Windows.ResourceDictionary> d’un contrôle personnalisé impose un impact sur les performances pour chaque instance de ce contrôle. Par exemple, si vous avez défini des opérations de pinceau gourmandes en performances dans le cadre de la définition de ressource d’un contrôle personnalisé et de nombreuses instances du contrôle personnalisé, la plage de travail de l’application augmente considérablement.  
  
 Pour illustrer ce point, prenez en compte les points suivants. Supposons que vous développiez un jeu de cartes à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour la plupart des jeux de cartes, vous avez besoin de 52 cartes avec 52 de faces différentes. Vous décidez d’implémenter un contrôle personnalisé de carte et vous définissez 52 pinceaux (chacun représentant un visage de carte) dans les ressources de votre contrôle personnalisé de carte. Dans votre application principale, vous créez initialement 52 instances de ce contrôle personnalisé de carte. Chaque instance du contrôle personnalisé de carte génère 52 instances de <xref:System.Windows.Media.Brush> objets, ce qui vous donne un total de 52 * 52 <xref:System.Windows.Media.Brush> objets de votre application. En déplaçant les pinceaux hors des ressources de contrôle personnalisé de la carte au niveau de l’objet <xref:System.Windows.Application> ou <xref:System.Windows.Window>, ou en les définissant dans le thème par défaut pour le contrôle personnalisé, vous réduisez la plage de travail de l’application, car vous partagez maintenant les pinceaux 52 entre les 52 instances du contrôle de carte.  
  
## <a name="sharing-a-brush-without-copying"></a>Partage d’un pinceau sans copie  
 Si vous avez plusieurs éléments qui utilisent le même <xref:System.Windows.Media.Brush> objet, définissez le pinceau en tant que ressource et référencez-le, plutôt que de définir le pinceau Inline en XAML. Cette méthode crée une instance et la réutilise, tandis que la définition de pinceaux inline dans XAML crée une nouvelle instance pour chaque élément.  
  
 L’exemple de balisage suivant illustre ce point :  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Utiliser des ressources statiques lorsque cela est possible  
 Une ressource statique fournit une valeur pour n’importe quel attribut de propriété XAML en recherchant une référence à une ressource déjà définie. Le comportement de recherche pour cette ressource est analogue à la recherche au moment de la compilation.  
  
 Une ressource dynamique, en revanche, crée une expression temporaire pendant la compilation initiale et, par conséquent, retarde la recherche des ressources jusqu’à ce que la valeur de ressource demandée soit réellement requise pour construire un objet. Le comportement de recherche pour cette ressource est analogue à la recherche au moment de l’exécution, ce qui impose un impact sur les performances. Utilisez des ressources statiques dans la mesure du possible dans votre application, à l’aide de ressources dynamiques uniquement lorsque cela est nécessaire.  
  
 L’exemple de balisage suivant montre l’utilisation des deux types de ressources :  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Texte](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
