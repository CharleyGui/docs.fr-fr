---
title: '{}Séquence d’évasion - Extension de Markup'
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
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071744"
---
# <a name="-escape-sequence--markup-extension"></a>{}Séquence d’évasion / extension de balisage

Fournit la séquence d’évacuation XAML pour les valeurs d’attribut. La séquence d’évacuation permet d’interpréter les valeurs ultérieures de l’attribut comme littérales.

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
|*littéralValue*|La chaîne littérale qui suit la séquence d’évasion. Typiquement, cette chaîne contient une accolade ouverte ou proche (ou' ).|

## <a name="remarks"></a>Notes

La séquence{}d’évacuation ( ) est utilisée de sorte qu’une accolade ouverte peut être utilisée comme personnage littéral dans XAML.

Les lecteurs de XAML utilisent généralement l’attelle ouverte pour désigner le point d’entrée d’une extension de balisage; cependant, ils vérifient d’abord le caractère suivant pour déterminer s’il s’agit d’une accolade de fermeture ( ). Ce n’est que{}lorsque les deux accolades ( ) sont adjacentes, qu’elles sont considérées comme une séquence d’évacuation.

Si la séquence d’évacuation est rencontrée, le lecteur XAML doit traiter le reste de la chaîne comme une chaîne. Toutefois, si la séquence d’échappement est appliquée à un membre qui a un convertisseur de type, la chaîne peut subir une conversion de type lorsqu’elle est interprétée par un auteur XAML.

La séquence d’évasion n’est pas une extension de balisage et n’est pas soutenue par une classe. Cependant, il s’agit d’une convention que les lecteurs XAML (y compris les lecteurs personnalisés XAML) devraient respecter.

Une marque de citation (") ne peut pas être utilisée comme séquence d’évasion de cette manière. Si vous avez besoin de définir une marque de de cotation comme valeur de propriété pour une propriété non contente, utilisez la syntaxe d’élément de propriété et placez la marque de citation comme chaîne à l’intérieur de l’élément de propriété, ou employez une entité de caractère XML. Pour une propriété de contenu, la marque de citation peut être l’ensemble du contenu.

La séquence{}d’évasion ( ) est fréquemment nécessaire lors de la spécalisation d’un type XML qui doit inclure un qualificatif namespace dans un endroit où une extension de balisage XAML peut apparaître. Cet emplacement comprend le début d’une valeur d’attribut XAML, et dans une extension de balisage immédiatement après un signe égal ( ). L’exemple suivant montre des séquences d’évasion pour un espace de nom XML qui apparaît au début d’une valeur d’attribut XAML.

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>Voir aussi

- [Convertisseurs de types et extensions de balisage pour XAML](type-converters-and-markup-extensions.md)
- [Entités de caractères XML et XAML](xml-character-entities.md)
