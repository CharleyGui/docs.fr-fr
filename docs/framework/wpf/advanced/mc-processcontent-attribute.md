---
title: mc:ProcessContent, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bcf55668bdc70902e346c401549a88f6ccb9072e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095123"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent, attribut
Spécifie les éléments de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doivent toujours avoir un contenu traité par des éléments parents pertinents, même si l’élément parent immédiat peut être ignoré par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en raison de la spécification de l' [attribut MC : Ignorable](mc-ignorable-attribute.md). L’attribut `mc:ProcessContent` prend en charge la compatibilité du balisage pour le mappage d’espace de noms personnalisé et pour le contrôle de version [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
```xaml  
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
|*ThisElementCanBeIgnored*|Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implémentations du processeur, si le type sous-jacent ne peut pas être résolu.|  
|*humidité*|*ThisElementCanBeIgnored* est marqué comme étant ignoré. Si le processeur ignore cet élément, *[content]* est traité par l' *objet*.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore le contenu d’un élément ignoré. Vous pouvez spécifier un élément spécifique par `mc:ProcessContent`, et un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] continuera à traiter le contenu dans l’élément ignoré. Cela est généralement utilisé si le contenu est imbriqué dans plusieurs balises, au moins l’une d’entre elles pouvant être Ignorable et au moins l’une d’entre elles ne peut pas être ignorée.  
  
 Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un séparateur d’espace, par exemple : `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 L’espace de noms `http://schemas.openxmlformats.org/markup-compatibility/2006` définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du kit de développement logiciel (SDK). Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Voir aussi

- [mc:Ignorable, attribut](mc-ignorable-attribute.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
