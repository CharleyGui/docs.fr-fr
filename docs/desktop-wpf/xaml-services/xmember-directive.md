---
title: x:Member, directive
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 1c5b26b405e574290af54b29b22fb5e19e4b6b95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548245"
---
# <a name="xmember-directive"></a>x:Member, directive
Déclare un membre XAML dans le balisage.

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`className`|Nom de la classe de stockage ou de la classe partielle pour la production XAML.|
|`memberName`|Nom de membre de la propriété définie.|

## <a name="remarks"></a>Notes

Dans l’implémentation des services XAML .NET,. `x:Member` n'a pas de stockage de type direct, mais est pris en charge par la classe <xref:System.Windows.Markup.MemberDefinition>. Dans un flux de nœud XAML, un élément `x:Member` est représenté en tant que membre nommé `Member`, à partir de l'espace de noms XAML du langage XAML. Le membre `Member` contient les attributs déclarés par le balisage.

La signification de `Name` et ne `Type` sont pas assignées au niveau des services XAML .net. Elles est stockée dans le flux de nœud XAML initial sous forme de valeur de chaîne, afin d’être interprétée ultérieurement selon les règles pouvant être imposées par les infrastructures spécifiques. La signification peut s'aligner sur celle d'un nom et d'un type XAML, ou être valide uniquement dans un système de type de stockage, selon l'implémentation.

Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable. Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`. Toutefois, le mécanisme d’association de types et de membres ou de génération de définitions de membres dynamiques n’est pas pris en charge au niveau des services XAML .NET. En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML. Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.

## <a name="xproperty-for-windows-workflow-foundation"></a>X:Property pour Windows Workflow Foundation

Pour Windows Workflow Foundation, `x:Property` définit les membres d'une activité personnalisée entièrement composée en XAML ou des membres dynamiques définis en XAML pour un ActivityDesigner avec code-behind. L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML. Ce n’est pas une exigence au niveau des services XAML .NET, mais elle devient une exigence lorsque la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général. Windows Workflow Foundation n’utilise pas le nom de type XAML pur comme valeur prévue pour l' `x:Property` `Type` attribut, et utilise à la place une convention qui n’est pas documentée ici. Pour plus d’informations, consultez [création de DynamicActivity](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
