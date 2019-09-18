---
title: x:Members, directive
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053767"
---
# <a name="xmembers-directive"></a>x:Members, directive
Contient un ensemble de membres définis dans le balisage, qui s’appliquent au x :Class de l’élément parent.  
  
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
|`oneOrMoreMembers`|Un ou plusieurs éléments objets qui représentent des définitions de membre. En règle générale, `x:Property` il s’agit d’éléments objet. Consultez la section Notes.|  
  
## <a name="remarks"></a>Notes  
 Dans l’implémentation des services XAML .NET Framework, il n’existe aucune classe de stockage ni aucune implémentation `x:Members`de membre sous-jacent pour. `x:Members`est un membre XAML spécial qui peut exister en tant que membre sur n’importe quel type. Dans un flux de nœud XAML `x:Members` , est représenté en tant que `Members`membre nommé, à partir de l’espace de noms XAML du langage XAML. Le membre `Members` contient une liste générique d' `Member` objets en lecture seule. Dans le balisage standard, les membres individuels `x:Property` sont spécifiés en tant qu’éléments de propriété. `x:Property`est un type plus précis spécifiquement pour les propriétés de types et peut être assigné `x:Member`à. Pour plus d’informations, consultez [directive x :Property](x-property-directive.md).  
  
 Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable. Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`. Toutefois, le mécanisme permettant d'associer des types et des membres ou de générer des définitions de membre dynamique n'est pas pris en charge au niveau des services XAML .NET Framework. En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML. Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>X :members, pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Members` contient les membres d’une activité personnalisée composée entièrement en XAML, ou des membres dynamiques définis en XAML pour un concepteur d’activités avec code-behind. L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML. Cela n'est pas obligatoire dans le cadre des services XAML .NET Framework, mais le devient quand la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et le XAML de Windows Workflow Foundation en général. `x:Members`doit être le premier élément enfant dans le balisage de l’élément objet qui déclare `x:Class`.
