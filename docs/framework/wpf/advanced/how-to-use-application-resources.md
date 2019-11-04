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
# <a name="how-to-use-application-resources"></a><span data-ttu-id="2071e-102">Guide pratique pour utiliser des ressources d’application</span><span class="sxs-lookup"><span data-stu-id="2071e-102">How to: Use Application Resources</span></span>
<span data-ttu-id="2071e-103">Cet exemple montre comment utiliser des ressources d’application.</span><span class="sxs-lookup"><span data-stu-id="2071e-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2071e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2071e-104">Example</span></span>  
 <span data-ttu-id="2071e-105">L’exemple suivant montre un fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="2071e-105">The following example shows an application definition file.</span></span> <span data-ttu-id="2071e-106">Le fichier de définition d’application définit une section de ressource (une valeur pour la propriété <xref:System.Windows.Application.Resources%2A>).</span><span class="sxs-lookup"><span data-stu-id="2071e-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="2071e-107">Les ressources définies au niveau de l’application sont accessibles à toutes les autres pages qui font partie de l’application.</span><span class="sxs-lookup"><span data-stu-id="2071e-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="2071e-108">Dans ce cas, la ressource est un style déclaré.</span><span class="sxs-lookup"><span data-stu-id="2071e-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="2071e-109">Étant donné qu’un style complet qui comprend un modèle de contrôle peut être long, cet exemple omet le modèle de contrôle qui est défini dans le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> accesseur Set de la propriété du style.</span><span class="sxs-lookup"><span data-stu-id="2071e-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="2071e-110">L’exemple suivant montre une page de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui fait référence à la ressource de niveau application que l’exemple précédent a définie.</span><span class="sxs-lookup"><span data-stu-id="2071e-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="2071e-111">La ressource est référencée à l’aide d’une [extension de balisage StaticResource](staticresource-markup-extension.md) qui spécifie la clé de ressource unique pour la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="2071e-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="2071e-112">Aucune ressource avec la clé « GelButton » ne figurant dans la page active, l’étendue de recherche de ressource pour la ressource demandée continue au-delà de la page active, dans les ressources définies au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="2071e-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="2071e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2071e-113">See also</span></span>

- [<span data-ttu-id="2071e-114">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="2071e-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="2071e-115">Vue d’ensemble de la gestion d’applications</span><span class="sxs-lookup"><span data-stu-id="2071e-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="2071e-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2071e-116">How-to Topics</span></span>](resources-how-to-topics.md)
