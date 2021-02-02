---
title: Réflexion (C#)
description: La réflexion fournit des objets qui décrivent les assemblys, les modules et les types en C#. Si votre code comprend des attributs, la réflexion vous permet d’y accéder.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 91d6d9bbd54199f3468f867d8804596f4a7546d9
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427059"
---
# <a name="reflection-c"></a>Réflexion (C#)

La réflexion fournit des objets (de type <xref:System.Type> ) qui décrivent les assemblys, les modules et les types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).

Voici un exemple simple de réflexion à l’aide de la <xref:System.Object.GetType> méthode, héritée par tous les types de la `Object` classe de base, pour obtenir le type d’une variable :

> [!NOTE]
> Veillez à ajouter `using System;` et `using System.Reflection;` en haut de votre fichier *. cs* .

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

La sortie est : `System.Int32` .

L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

La sortie est : `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` .

> [!NOTE]
> Les mots clés C# `protected` et n' `internal` ont aucune signification en langage intermédiaire (il) et ne sont pas utilisés dans les API de réflexion. Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*. Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>. Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Vue d’ensemble de la réflexion

La réflexion est utile dans les situations suivantes :

- Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme. Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Pour examiner et instancier des types dans un assembly.
- Pour créer de nouveaux types au moment de l’exécution. Utilisez des classes dans <xref:System.Reflection.Emit>.
- Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution. Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Sections connexes

Pour plus d'informations :

- [Réflexion](../../../framework/reflection-and-codedom/reflection.md)
- [Affichage des informations de type](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Réflexion et types génériques](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
