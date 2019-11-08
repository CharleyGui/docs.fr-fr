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
ms.openlocfilehash: e14ab0ebc7d44e2792307b16c7c0581ff7a71bc6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740821"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable, attribut
Spécifie les préfixes d’espaces de noms XML rencontrés dans un fichier de balisage qui peuvent être ignorés par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. L’attribut `mc:Ignorable` prend en charge la compatibilité du balisage pour le mappage d’espace de noms personnalisé et pour le contrôle de version [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
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
|*ThisElementCanBeIgnored*|Élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implémentations du processeur, si le type sous-jacent ne peut pas être résolu.|  
  
## <a name="remarks"></a>Notes  
 Le préfixe d’espace de noms XML `mc` est la Convention de préfixe recommandée à utiliser lors du mappage de l’espace de noms de compatibilité [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `http://schemas.openxmlformats.org/markup-compatibility/2006`.  
  
 Éléments ou attributs où la partie préfixe du nom de l’élément est identifiée comme `mc:Ignorable` ne déclenchera pas d’erreurs en cas de traitement par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Si cet attribut n’a pas pu être résolu en un type sous-jacent ou une construction de programmation, cet élément est ignoré. Notez cependant que les éléments ignorés peuvent toujours générer des erreurs d’analyse supplémentaires pour des spécifications d’éléments supplémentaires qui sont des effets secondaires de cet élément qui ne sont pas traités. Par exemple, un modèle de contenu d’élément particulier peut nécessiter exactement un élément enfant, mais si l’élément enfant spécifié se trouvait dans un préfixe `mc:Ignorable` et que l’élément enfant spécifié n’a pas pu être résolu en un type, le processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut déclencher une erreur.  
  
 `mc:Ignorable` s’applique uniquement aux mappages d’espaces de noms aux chaînes d’identificateur. `mc:Ignorable` ne s’applique pas aux mappages d’espaces de noms dans les assemblys, qui spécifient un espace de noms CLR et un assembly (ou l’exécutable actuel comme assembly).  
  
 Si vous implémentez un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], votre implémentation de processeur ne doit pas déclencher d’erreurs d’analyse ou de traitement sur la résolution de type pour tout élément ou attribut qualifié par un préfixe identifié comme `mc:Ignorable`. Toutefois, votre implémentation de processeur peut toujours lever des exceptions qui sont un résultat secondaire d’un élément qui n’a pas pu être chargé ou traité, tel que l’exemple d’élément enfant donné précédemment.  
  
 Par défaut, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore le contenu d’un élément ignoré. Toutefois, vous pouvez spécifier un attribut supplémentaire, [MC : ProcessContent](mc-processcontent-attribute.md), pour exiger le traitement continu du contenu dans un élément ignoré par l’élément parent disponible suivant.  
  
 Plusieurs préfixes peuvent être spécifiés dans l’attribut, en utilisant un ou plusieurs espaces blancs comme séparateur, par exemple : `mc:Ignorable="ignore1 ignore2"`.  

 L’espace de noms `http://schemas.openxmlformats.org/markup-compatibility/2006` définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone du kit de développement logiciel (SDK). Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze, attribut](presentationoptions-freeze-attribute.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Documents dans WPF](documents-in-wpf.md)
