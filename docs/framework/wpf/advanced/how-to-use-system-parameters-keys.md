---
title: 'Procédure : Utiliser des clés de paramètres système'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918369"
---
# <a name="how-to-use-system-parameters-keys"></a>Procédure : Utiliser des clés de paramètres système
Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels cohérents avec les paramètres système. <xref:System.Windows.SystemParameters>est une classe qui contient à la fois des valeurs de paramètre système et des clés de ressource qui sont liées <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> aux <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>valeurs, par exemple et. Les métriques de paramètres système peuvent être utilisées en tant que ressources statiques ou dynamiques. Utilisez une ressource dynamique si vous souhaitez que les métriques de paramètres soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une ressource statique.  
  
> [!NOTE]
> Les ressources dynamiques ont une *clé* de mot clé ajoutée au nom de la propriété.  
  
 L’exemple suivant montre comment accéder à des ressources dynamiques de paramètres système et comment les utiliser pour personnaliser un bouton ou lui appliquer un style. Cet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple dimensionne un bouton en <xref:System.Windows.SystemParameters> affectant des valeurs à la largeur et à la hauteur du bouton.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Voir aussi

- [Peindre une zone avec un pinceau système](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Utiliser des SystemFonts](how-to-use-systemfonts.md)
- [Utiliser SystemParameters](how-to-use-systemparameters.md)
