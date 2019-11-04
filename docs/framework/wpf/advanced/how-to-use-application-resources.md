---
title: Guide pratique pour utiliser des ressources d’application
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460269"
---
# <a name="how-to-use-application-resources"></a>Guide pratique pour utiliser des ressources d’application
Cet exemple montre comment utiliser des ressources d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un fichier de définition d’application. Le fichier de définition d’application définit une section de ressource (une valeur pour la propriété <xref:System.Windows.Application.Resources%2A>). Les ressources définies au niveau de l’application sont accessibles à toutes les autres pages qui font partie de l’application. Dans ce cas, la ressource est un style déclaré. Étant donné qu’un style complet qui comprend un modèle de contrôle peut être long, cet exemple omet le modèle de contrôle qui est défini dans le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> accesseur Set de la propriété du style.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 L’exemple suivant montre une page de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui fait référence à la ressource de niveau application que l’exemple précédent a définie. La ressource est référencée à l’aide d’une [extension de balisage StaticResource](staticresource-markup-extension.md) qui spécifie la clé de ressource unique pour la ressource demandée. Aucune ressource avec la clé « GelButton » ne figurant dans la page active, l’étendue de recherche de ressource pour la ressource demandée continue au-delà de la page active, dans les ressources définies au niveau de l’application.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Vue d’ensemble de la gestion d’applications](../app-development/application-management-overview.md)
- [Rubriques de guide pratique](resources-how-to-topics.md)
