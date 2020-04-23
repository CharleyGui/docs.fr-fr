---
title: Assemblys pouvant être collectés pour la génération de type dynamique
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 02c7048e0321282463aa3558287d1d13c5e4f8d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180544"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Assemblys pouvant être collectés pour la génération de type dynamique

Les *assemblys pouvant être collectés* sont des assemblys dynamiques qui peuvent être déchargés sans décharger le domaine d’application dans lequel ils ont été créés. Toute la mémoire managée et non managée utilisée par un assembly pouvant être collecté et les types qu’il contient peuvent être récupérés. Les informations telles que le nom de l’assembly sont supprimées des tables internes.

Pour activer le déchargement, utilisez l’indicateur <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> quand vous créez un assembly dynamique. L’assembly est transitoire (autrement dit, il ne peut pas être enregistré) et est soumis aux limitations décrites dans la section [Restrictions sur les assemblys pouvant être collectés](#restrictions-on-collectible-assemblies). Le common language runtime (CLR) décharge automatiquement un assembly pouvant être collecté lors de la mise en production de tous les objets associés à l’assembly. Sous tous les autres aspects, les assemblys pouvant être collectés sont créés et utilisés de la même façon que d’autres assemblys dynamiques.

## <a name="lifetime-of-collectible-assemblies"></a>Durée de vie des assemblys pouvant être collectés

La durée de vie d’un assembly pouvant être collecté est contrôlée par l’existence de références aux types qu’il contient et aux objets qui sont créés à partir de ces types. Le common language runtime ne décharge pas d’assembly tant qu’un ou que plusieurs des éléments suivants existent (`T` correspond à tout type qui est défini dans l’assembly) :

- Instance de `T`.

- Instance d’un tableau de `T`.

- Instance d’un type générique qui a `T` comme l’un de ses arguments de type. Cela inclut les collections génériques de `T`, même si cette collection est vide.

- Instance de <xref:System.Type> ou <xref:System.Reflection.Emit.TypeBuilder> qui représente `T`.

   > [!IMPORTANT]
   > Vous devez libérer tous les objets qui représentent des parties de l’assembly. <xref:System.Reflection.Emit.ModuleBuilder> qui définit `T` conserve une référence à <xref:System.Reflection.Emit.TypeBuilder>, et l’objet <xref:System.Reflection.Emit.AssemblyBuilder> conserve une référence à <xref:System.Reflection.Emit.ModuleBuilder>, de sorte que les références à ces objets doivent être libérées. Même l’existence d’un <xref:System.Reflection.Emit.LocalBuilder> ou <xref:System.Reflection.Emit.ILGenerator> utilisé dans la construction de `T` empêche le déchargement.

- Référence statique à `T` par un autre type défini dynamiquement `T1` qui est encore accessible par l’exécution de code. Par exemple, `T1` peut dériver de `T`, ou `T` peut être le type d’un paramètre dans une méthode de `T1`.

- **ByRef** pour un champ statique qui appartient à `T`.

- <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle> ou <xref:System.RuntimeMethodHandle> qui fait référence à `T` ou à un composant de `T`.

- Instance de tout objet reflection qui peut être utilisée indirectement ou directement pour accéder à l’objet <xref:System.Type> qui représente `T`. Par exemple, l’objet <xref:System.Type> pour `T` peut être obtenu à partir d’un type tableau dont le type d’élément est `T`, ou à partir d’un type générique qui a `T` comme argument de type.

- Méthode `M` sur la pile des appels de tout thread, où `M` est une méthode de `T` ou une méthode de niveau module qui est définie dans l’assembly.

- Délégué d’une méthode statique qui est définie dans un module de l’assembly.

Si un seul élément de cette liste existe pour un seul type ou une seule méthode dans l’assembly, le runtime ne peut pas décharger l’assembly.

> [!NOTE]
> Le runtime ne décharge pas réellement l’assembly tant que les finaliseurs n’ont pas été exécutés pour tous les éléments de la liste.

À des fins de suivi de durée de vie, un type générique construit comme `List<int>` (en C#) ou `List(Of Integer)` (en Visual Basic), qui est créé et utilisé dans la génération d’un assembly pouvant être collecté est considéré comme ayant été défini dans l’assembly qui contient la définition de type générique ou dans un assembly qui contient la définition de l’un de ses arguments de type. L’assembly exact utilisé est un détail d’implémentation et est susceptible de changer.

## <a name="restrictions-on-collectible-assemblies"></a>Restrictions sur les assemblys pouvant être collectés

Les restrictions suivantes s’appliquent aux assemblys pouvant être collectés :

- **Références statiques** Les types d’un assembly dynamique ordinaire ne peuvent pas avoir de références statiques à des types définis dans un assembly pouvant être collecté. Par exemple, si vous définissez un type simple qui hérite d’un type dans un assembly pouvant être collecté, une exception <xref:System.NotSupportedException> est levée. Un type dans un assembly pouvant être collecté peut avoir des références statiques à un type dans un autre assembly pouvant être collecté, mais cela permet d’étendre la durée de vie de l’assembly référencé à la durée de vie de l’assembly de référence.

- **COM Interop** Aucune interface COM ne peut être définie dans un assembly pouvant être collecté, et aucune instance de type dans un assembly pouvant être collecté ne peut être convertie en objets COM. Un type dans un assembly pouvant être collecté ne peut pas servir de wrapper CCW (COM Callable Wrapper) ni de wrapper RCW (Runtime Callable Wrapper). Toutefois, les types dans les assemblys pouvant être collectés peuvent utiliser des objets qui implémentent les interfaces COM.

- **Appel** de code non managé Les méthodes qui ont <xref:System.Runtime.InteropServices.DllImportAttribute> l’attribut ne sont pas compilées quand elles sont déclarées dans un assembly pouvant être collecté. L’instruction <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> ne peut pas être utilisée dans l’implémentation d’un type dans un assembly pouvant être collecté, et ces types ne peuvent pas être marshalés en code non managé. Toutefois, vous pouvez effectuer un appel en code natif à l’aide d’un point d’entrée qui est déclaré dans un assembly ne pouvant pas être collecté.

- **Marshaling** Les objets (en particulier, les délégués) définis dans les assemblys pouvant être collectés ne peuvent pas être marshalés. Il s’agit d’une restriction sur tous les types émis transitoires.

- **Chargement d’assembly** L’émission de réflexion est le seul mécanisme pris en charge pour le chargement des assemblys pouvant être collectés. Les assemblys chargés à l’aide de toute autre forme de chargement d’assembly ne peuvent pas être déchargés.

- **Objets liés au contexte** Les variables statiques de contexte ne sont pas prises en charge. Les types dans un assembly pouvant être collecté ne peuvent pas étendre <xref:System.ContextBoundObject>. Toutefois, le code dans les assemblys pouvant être collectés peut utiliser des objets liés au contexte définis ailleurs.

- **Données statiques de thread** Les variables statiques de thread ne sont pas prises en charge.

## <a name="see-also"></a>Voir aussi

- [Émission d’assemblys et de méthodes dynamiques](emitting-dynamic-methods-and-assemblies.md)
