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
ms.openlocfilehash: 837a18ca18d0c634dfa5cc133aa013919cfb9d96
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053897"
---
# <a name="xamlname-grammar"></a>XamlName, grammaire
La grammaire XamlName est une grammaire spécifique qui est définie dans la spécification du langage XAML [MS-XAML], qui est reproduite ici pour des raisons pratiques.  
  
## <a name="from-the-xaml-specification"></a>À partir de la spécification XAML  
 La spécification [MS-XAML] définit la grammaire XamlName pour identifier le jeu d’identificateurs symboliques légaux utilisé pour les types et les propriétés.  
  
 Les valeurs de chaîne qui sont de type XamlName doivent respecter la grammaire suivante :  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Qui utilise les valeurs de catégorie générale suivantes, telles que définies dans la base de données de caractères Unicode  

| Catégorie Unicode   | Description                   |
|--------------------|-------------------------------|
| Lu                 | Letter, Uppercase             |
| Ll                 | Letter, Lowercase             |
| Lt                 | Letter, Titlecase             |
| Lm                 | Letter, Modifier              |
| Lo                 | Letter, Other                 |
| Mn                 | Marquer, sans espace             |
| Mc                 | Mark, Spacing Combining       |
| Nd                 | Nombre, décimal               |
| Nl                 | Number, Letter                |
 
 XAML définit une deuxième grammaire, DottedXamlName, qui est utilisée pour les références qualifiées de propriété et d’événement, ainsi que pour les membres attachés. Pour plus d’informations, <xref:System.Windows.DependencyProperty> consultez et [vue d’ensemble du langage XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md).  
  
 Les valeurs de chaîne qui sont de type DottedXamlName doivent être conformes à la grammaire suivante :  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Notes  
 Pour obtenir la spécification complète, consultez [ \[MS-\]XAML](https://go.microsoft.com/fwlink/?LinkId=114525).
