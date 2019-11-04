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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459945"
---
# <a name="xnull-markup-extension"></a>x:Null, extension de balisage
Spécifie `null` en tant que valeur d’un membre XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Notes  
 Le mot clé pour une référence null C# dans C++ et est null. Le mot clé Microsoft Visual Basic pour une référence null est `Nothing`, mais vous utilisez toujours `{x:Null}` comme utilisation XAML, quel que soit le langage code-behind que vous associez au XAML.  
  
 L’extension de balisage `x:Null` n’a pas de propriétés définissables.  
  
 Une utilisation null est souvent associée à l’exposition du membre XAML d’une valeur de <xref:System.Nullable%601> CLR.  
  
 L’extension de balisage `x:Null`, comme toutes les extensions de balisage XAML, utilise les accolades (`{,}`) pour placer dans une séquence d’échappement la gestion des valeurs d’attribut pour être autres que des littéraux ou des références de gestionnaire d’événements. La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Une syntaxe d’élément objet `<x:Null />` est techniquement possible, mais est rarement utilisée, car l’extension de balisage `x:Null` n’a pas de paramètres positionnels ou d’arguments de construction.  
  
 Pour plus d’informations sur les extensions de balisage, consultez [extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Dans .NET Framework services XAML, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.NullExtension>.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Notez que `null` n’est pas nécessairement la valeur non définie initiale pour une propriété de dépendance de type référence. La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur des métadonnées spécifiques à la propriété. De nombreuses propriétés de dépendance n’acceptent pas `null` comme valeur, par le biais du balisage ou du code en raison de leurs implémentations de rappel de validation. Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
