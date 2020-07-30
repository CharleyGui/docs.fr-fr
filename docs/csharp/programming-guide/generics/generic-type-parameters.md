---
title: Paramètres de type générique - Guide de programmation C#
description: En savoir plus sur la définition de type générique en C#, où un paramètre de type est un espace réservé pour un type que le client spécifie pour une instance du type générique.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: dc37029378ac1e9ec194d95b561787761d69a9fd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299251"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Paramètres de type générique (Guide de programmation C#)

Dans une définition de méthode ou de type générique, le paramètre de type représente un espace réservé pour un type spécifié par le client au moment de créer une instance du type générique. Une classe générique, telle que `GenericList<T>` répertoriée dans [Introduction aux génériques](./index.md), ne peut pas être utilisée en l’état car il ne s’agit pas vraiment d’un type, mais plutôt d’un modèle pour un type. Pour utiliser `GenericList<T>`, le code client doit déclarer et instancier un type construit en spécifiant un argument de type à l’intérieur de crochets pointus. L’argument de type pour cette classe particulière peut être tout type reconnu par le compilateur. Il est possible de créer un nombre quelconque d’instances de type construit, chacune avec un argument de type différent, comme suit :  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
Dans chacune de ces instances de `GenericList<T>`, chaque occurrence de `T` dans la classe est remplacée à l’exécution par l’argument de type. Par cette substitution, nous avons créé trois objets distincts de type sécurisé et efficaces à l’aide d’une seule définition de classe. Pour plus d’informations sur la façon dont cette substitution est exécutée par le CLR, consultez [Génériques dans le runtime](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Recommandations concernant le nom des paramètres de type  
  
- **Nommez** les paramètres de type générique avec des noms descriptifs, sauf si un nom composé d’une seule lettre est suffisamment évocateur et qu’un nom descriptif n’apporte rien de plus.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Envisagez** l’utilisation de T comme nom de paramètre de type pour les types ayant un paramètre de type d’une seule lettre.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Préfixez** les noms des paramètres de type descriptifs avec « T ».  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Pensez** à indiquer les contraintes placées sur un paramètre de type dans le nom de paramètre. Par exemple, un paramètre limité à `ISession` peut être appelé `TSession`.

La règle d’analyse du code [CA1715](/visualstudio/code-quality/ca1715) vérifie que les paramètres de type sont correctement nommés.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Génériques](./index.md)
- [Différences entre les modèles C++ et les génériques C#](./differences-between-cpp-templates-and-csharp-generics.md)
