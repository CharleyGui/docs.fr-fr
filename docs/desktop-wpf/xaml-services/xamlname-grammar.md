---
title: XamlName, grammaire
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071828"
---
# <a name="xamlname-grammar"></a>XamlName, grammaire

XamlName Grammar est une grammaire spécifique qui est définie dans la spécification de la langue XAML [MS-XAML], qui est reproduit ici pour plus de commodité.

## <a name="from-the-xaml-specification"></a>De la spécification XAML

La spécification [MS-XAML] définit la grammaire XamlName pour identifier l’ensemble des identificateurs symboliques juridiques utilisés pour les types et les propriétés.

Les valeurs de chaîne de type XamlName doivent se conformer à la grammaire suivante :

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

Ce qui suppose les valeurs de catégorie générale suivantes telles que définies dans la base de données sur les caractères Unicode

| Catégorie Unicode   | Description                   |
|--------------------|-------------------------------|
| Lu                 | Letter, Uppercase             |
| Ll                 | Letter, Lowercase             |
| Lt                 | Letter, Titlecase             |
| Lm                 | Letter, Modifier              |
| Lo                 | Letter, Other                 |
| Mn                 | Marque, Non-Spacing             |
| Mc                 | Mark, Spacing Combining       |
| Nd                 | Nombre, Décimale               |
| Nl                 | Number, Letter                |

XAML définit une deuxième grammaire, DottedXamlName, qui est utilisée pour les références qualifiées de propriété et d’événement, et aussi pour les membres ci-joints. Pour plus d’informations, voir <xref:System.Windows.DependencyProperty> et [XAML Aperçu (WPF)](../fundamentals/xaml.md).

Les valeurs de chaîne qui sont de type DottedXamlName doivent se conformer à la grammaire suivante :

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Notes

Pour les spécifications complètes, voir [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
