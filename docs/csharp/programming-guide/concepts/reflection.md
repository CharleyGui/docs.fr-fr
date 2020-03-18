---
title: Réflexion (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711659"
---
# <a name="reflection-c"></a>Réflexion (C#)

Réflexion fournit des <xref:System.Type>objets (de type) qui décrivent les assemblages, les modules et les types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés. Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder. Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).

Voici un exemple simple de <xref:System.Object.GetType> réflexion utilisant la méthode `Object` - héritée par tous les types de la classe de base - pour obtenir le type de variable :

> [!NOTE]
> Assurez-vous `using System;` d’ajouter et `using System.Reflection;` en haut de votre fichier *.cs.*

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

La sortie `System.Int32`est: .

L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

La sortie `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`est: .

> [!NOTE]
> Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion. Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*. Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>. Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Aperçu de la réflexion

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

- [Guide de programmation C#](../index.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
