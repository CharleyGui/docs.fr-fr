---
title: x:Null, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484709"
---
# <a name="xnull-markup-extension"></a>x:Null, extension de balisage
Spécifie `null` comme valeur pour un membre XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Notes  
 Le mot clé pour une référence null C# dans C++ et est null. Le mot clé Microsoft Visual Basic pour une référence null `Nothing`est, mais vous utilisez `{x:Null}` toujours comme utilisation XAML quel que soit le langage code-behind que vous associez au XAML.  
  
 L' `x:Null` extension de balisage n’a pas de propriétés définissables.  
  
 Une utilisation null est souvent associée à l’exposition du membre XAML d’une <xref:System.Nullable%601> valeur CLR.  
  
 L' `x:Null` extension de balisage, comme toutes les extensions de balisage XAML,`{,}`utilise les accolades () pour échapper la gestion des valeurs d’attribut à d’autres littéraux ou références de gestionnaires d’événements. La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Une syntaxe `<x:Null />` d’élément objet est techniquement possible, mais est rarement utilisée, `x:Null` car l’extension de balisage n’a pas de paramètres positionnels ou d’arguments de construction.  
  
 Pour plus d’informations sur les extensions de balisage, consultez [extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Dans .NET Framework services XAML, la gestion de cette extension de balisage est définie <xref:System.Windows.Markup.NullExtension> par la classe.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Notez qu' `null` il ne s’agit pas nécessairement de la valeur initiale non définie pour une propriété de dépendance de type référence. La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété. De nombreuses propriétés de dépendance n' `null` acceptent pas comme valeur, par le biais du balisage ou du code en raison de leurs implémentations de rappel de validation. Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Vue d’ensemble du langage XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
