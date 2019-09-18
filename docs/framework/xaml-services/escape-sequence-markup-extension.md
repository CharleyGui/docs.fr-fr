---
title: '{}Séquence d’échappement-extension de balisage'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053876"
---
# <a name="-escape-sequence--markup-extension"></a>{} Séquence d’échappement/Extension de balisage
Fournit la séquence d’échappement XAML pour les valeurs d’attribut. La séquence d’échappement permet d’interpréter les valeurs suivantes dans l’attribut comme un littéral.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Utilisation des éléments de propriété XAML  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*literalValue*|Chaîne littérale qui suit la séquence d’échappement. En général, cette chaîne contient une accolade ouvrante ou fermante ({ou}).|  
  
## <a name="remarks"></a>Notes  
 La séquence d’échappement{}() est utilisée pour qu’une accolade ouvrante ({) puisse être utilisée comme caractère littéral en XAML.  
  
 Les lecteurs XAML utilisent généralement l’accolade ouvrante ({) pour désigner le point d’entrée d’une extension de balisage ; Toutefois, ils vérifient d’abord le caractère suivant pour déterminer s’il s’agit d’une accolade fermante (}). La seule fois lorsque les deux accolades ({}) sont adjacentes, elles sont considérées comme une séquence d’échappement.  
  
 Si la séquence d’échappement est rencontrée, le lecteur XAML doit traiter le reste de la chaîne comme une chaîne. Toutefois, si la séquence d’échappement est appliquée à un membre qui possède un convertisseur de type, la chaîne peut subir une conversion de type lorsqu’elle est interprétée par un writer XAML.  
  
 La séquence d’échappement n’est pas une extension de balisage et n’est pas sauvegardée par une classe. Toutefois, il est recommandé de respecter les lecteurs XAML (y compris les lecteurs XAML personnalisés).  
  
 Un guillemet (") ne peut pas être utilisé comme une séquence d’échappement de cette manière. Si vous devez définir un guillemet comme valeur de propriété pour une propriété qui n’est pas de contenu, utilisez la syntaxe d’élément de propriété et placez le guillemet en tant que chaîne à l’intérieur de l’élément de propriété, ou utilisez une entité de caractère XML. Pour une propriété de contenu, le guillemet peut correspondre à tout le contenu.  
  
 La séquence d’échappement{}() est souvent requise lors de la spécification d’un type XML qui doit inclure un qualificateur d’espace de noms dans un emplacement où une extension de balisage XAML peut apparaître. Cela comprend le début d’une valeur d’attribut XAML, et dans une extension de balisage, immédiatement après un signe égal (=). L’exemple suivant montre des séquences d’échappement pour un espace de noms XML qui apparaît au début d’une valeur d’attribut XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Voir aussi

- [Convertisseurs de types et extensions de balisage pour XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Entités de caractères XML et XAML](xml-character-entities-and-xaml.md)
