---
title: x:Members, directive
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071464"
---
# <a name="xmembers-directive"></a>x:Members, directive
Détient un ensemble de membres qui sont définis dans la majoration, qui s’appliquent à la x:Class de l’élément parent.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`className`|Nom de la classe de stockage ou de la classe partielle pour la production XAML. Consultez la section Notes.|
|`oneOrMoreMembers`|Un ou plusieurs éléments d’objet qui représentent les définitions des membres. Typiquement, ce `x:Property` sont des éléments d’objet. Consultez la section Notes.|

## <a name="remarks"></a>Notes

Dans la mise en œuvre de .NET XAML Services, il n’y a pas de classe de soutien ou de mise en œuvre sous-jacente des membres pour `x:Members`. `x:Members`est un membre spécial XAML qui peut exister en tant que membre sur n’importe quel type. Dans un flux de nœuds XAML, `x:Members` est représenté en tant que membre nommé `Members`, à partir de la langue XAML XAML namespace. Le `Members` membre contient une liste `Member` générique d’objets non sur la seule lecture. Dans la balisage typique, `x:Property` les membres individuels sont spécifiés comme éléments de propriété. `x:Property`est un type plus précis spécifiquement pour les `x:Member`propriétés de types et est assignable à . Pour plus d’informations, voir [x:Property Directive](xproperty-directive.md).

Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable. Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`. Cependant, le mécanisme d’association des types et des membres ou pour produire des définitions dynamiques des membres n’est pas pris en charge au niveau .NET XAML Services. En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML. Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.

## <a name="xmembers-for-windows-workflow-foundation"></a>x:Membres pour Windows Workflow Foundation

Pour Windows Workflow `x:Members` Foundation, contient les membres d’une activité personnalisée entièrement composée en XAML, ou XAML - membres dynamiques définis pour un concepteur d’activité avec code-derrière. L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML. Ce n’est pas une exigence au niveau .NET XAML Services, mais devient une exigence lorsque la production XAML est chargée par le MSBUILD construire des actions qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général. `x:Members`doit être le premier élément enfant dans la majoration de l’élément objet qui déclare le `x:Class`.
