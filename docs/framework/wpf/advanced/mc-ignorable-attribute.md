---
title: mc:Ignorable, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: a72b2886c63a80a4887aa16fc6a952fa837a800f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991446"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable, attribut
Spécifie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les préfixes d’espaces de noms rencontrés dans un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage qui peuvent être ignorés par un processeur. L' `mc:Ignorable` attribut prend en charge la compatibilité du balisage pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mappage d’espace de noms personnalisé et pour le contrôle de version.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Utilisation des attributs XAML (préfixe unique)  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Utilisation des attributs XAML (deux préfixes)  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1, etc.*|Toute chaîne de préfixe valide, conformément à la spécification XML 1,0.|  
|*ignorableUri*|Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1,0.|  
|*ThisElementCanBeIgnored*|Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] les implémentations de processeur, si le type sous-jacent ne peut pas être résolu.|  
  
## <a name="remarks"></a>Notes  
 Le `mc` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `http://schemas.openxmlformats.org/markup-compatibility/2006`préfixe d’espace de noms est la Convention de préfixe recommandée à utiliser lors du mappage de l’espace de noms de compatibilité. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
 Les éléments ou les attributs où la partie préfixe du nom d’élément `mc:Ignorable` est identifiée comme ne déclenchent pas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’erreurs lorsqu’elles sont traitées par un processeur. Si cet attribut n’a pas pu être résolu en un type sous-jacent ou une construction de programmation, cet élément est ignoré. Notez cependant que les éléments ignorés peuvent toujours générer des erreurs d’analyse supplémentaires pour des spécifications d’éléments supplémentaires qui sont des effets secondaires de cet élément qui ne sont pas traités. Par exemple, un modèle de contenu d’élément particulier peut nécessiter exactement un élément enfant, mais si l’élément enfant spécifié `mc:Ignorable` se trouvait dans un préfixe et que l’élément enfant spécifié n’a pas pu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] être résolu en un type, le processeur peut génère une erreur.  
  
 `mc:Ignorable`s’applique uniquement aux mappages d’espaces de noms aux chaînes d’identificateur. `mc:Ignorable`ne s’applique pas aux mappages d’espaces de noms dans les assemblys, qui spécifient un espace de noms CLR et un assembly (ou l’exécutable actuel comme assembly).  
  
 Si vous implémentez un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, votre implémentation de processeur ne doit pas déclencher d’erreurs d’analyse ou de traitement sur la résolution de type pour tout élément ou attribut qualifié par un préfixe identifié comme. `mc:Ignorable` Toutefois, votre implémentation de processeur peut toujours lever des exceptions qui sont un résultat secondaire d’un élément qui n’a pas pu être chargé ou traité, tel que l’exemple d’élément enfant donné précédemment.  
  
 Par défaut, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ignore le contenu d’un élément ignoré. Toutefois, vous pouvez spécifier un attribut supplémentaire, [MC: ProcessContent](mc-processcontent-attribute.md), pour exiger le traitement continu du contenu dans un élément ignoré par l’élément parent disponible suivant.  
  
 Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un ou de plusieurs espaces blancs comme séparateur, `mc:Ignorable="ignore1 ignore2"`par exemple:.  

 L' `http://schemas.openxmlformats.org/markup-compatibility/2006` espace de noms définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du kit de développement logiciel (SDK). Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze, attribut](presentationoptions-freeze-attribute.md)
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
