---
title: x:Property, directive
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071408"
---
# <a name="xproperty-directive"></a>x:Property, directive

Déclare une propriété XAML dans le balisage.

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`className`|Nom de la classe de stockage ou de la classe partielle pour la production XAML.|
|`propertyName`|Nom de membre de la propriété définie.|
|`propertyType`|Tapez le nom (ou une autre forme de chaîne, propre à l'infrastructure) qui spécifie le type de cette propriété.|

## <a name="remarks"></a>Notes

Dans .NET XAML Services mise en œuvre, . `x:Property` n'a pas de stockage de type direct, mais est pris en charge par la classe <xref:System.Windows.Markup.PropertyDefinition>. Dans un flux de nœud XAML, un élément `x:Property` est représenté en tant que membre nommé `Property`, à partir de l'espace de noms XAML du langage XAML. Le membre `Property` contient les attributs déclarés par le balisage.

Le sens `Name` `Type` et ne sont pas attribués au niveau .NET XAML Services. Elles est stockée dans le flux de nœud XAML initial sous forme de valeur de chaîne, afin d’être interprétée ultérieurement selon les règles pouvant être imposées par les infrastructures spécifiques. La signification peut s'aligner sur celle d'un nom et d'un type XAML, ou être valide uniquement dans un système de type de stockage, selon l'implémentation.

Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable. Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`. Cependant, le mécanisme d’association des types et des membres ou pour produire des définitions dynamiques des membres n’est pas pris en charge au niveau .NET XAML Services. En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML. Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.

## <a name="xproperty-for-windows-workflow-foundation"></a>X:Property pour Windows Workflow Foundation

Pour Windows Workflow Foundation, `x:Property` définit les membres d'une activité personnalisée entièrement composée en XAML ou des membres dynamiques définis en XAML pour un ActivityDesigner avec code-behind. L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML. Ce n’est pas une exigence au niveau .NET XAML Services, mais devient une exigence lorsque la production XAML est chargée par le MSBUILD construire des actions qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général. Windows Workflow Foundation n’utilise pas le nom de type `x:Property` `Type` XAML pur comme valeur prévue pour l’attribut, et utilise plutôt une convention qui n’est pas documentée ici. Pour plus d’informations, voir [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
