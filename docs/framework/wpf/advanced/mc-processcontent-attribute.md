---
title: mc:ProcessContent, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 619c3ffbc68c8c72ea9dd6545ab8da536380483b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206169"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent, attribut
Spécifie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les éléments dont le contenu doit toujours être traité par les éléments parents pertinents, même si l’élément parent immédiat peut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] être ignoré par un processeur en raison de la spécification de l' [attribut MC: Ignorable](mc-ignorable-attribute.md). L' `mc:ProcessContent` attribut prend en charge la compatibilité du balisage pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mappage d’espace de noms personnalisé et pour le contrôle de version.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*ignorablePrefix*|Toute chaîne de préfixe valide, conformément à la spécification XML 1,0.|  
|*ignorableUri*|Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1,0.|  
|*ThisElementCanBeIgnored*|Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] les implémentations de processeur, si le type sous-jacent ne peut pas être résolu.|  
|*[content]*|*ThisElementCanBeIgnored* est marqué comme étant ignoré. Si le processeur ignore cet élément, *[content]* est traité par l' *objet*.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ignore le contenu d’un élément ignoré. Vous pouvez spécifier un élément spécifique par `mc:ProcessContent`et un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur continuera à traiter le contenu dans l’élément ignoré. Cela est généralement utilisé si le contenu est imbriqué dans plusieurs balises, au moins l’une d’entre elles pouvant être Ignorable et au moins l’une d’entre elles ne peut pas être ignorée.  
  
 Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un séparateur `mc:ProcessContent="ignore:Element1 ignore:Element2"`d’espace, par exemple:.  
  
 L' `http://schemas.openxmlformats.org/markup-compatibility/2006` espace de noms définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du kit de développement logiciel (SDK). Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Voir aussi

- [mc:Ignorable, attribut](mc-ignorable-attribute.md)
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
