---
title: 'Procédure : charger des assemblys dans le contexte de réflexion uniquement'
description: Consultez un exemple de chargement d’assemblys dans le contexte de réflexion uniquement dans .NET. Examinez les assemblys compilés pour d’autres plateformes ou versions .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865071"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Procédure : charger des assemblys dans le contexte de réflexion uniquement

Le contexte de chargement de réflexion uniquement permet d’examiner des assemblys compilés pour d’autres plateformes ou d’autres versions du .NET Framework. Le code chargé dans ce contexte peut uniquement être examiné. Il ne peut pas être exécuté. Cela signifie que les objets ne peuvent pas être créés, car les constructeurs ne peut pas être exécutés. Le code ne pouvant pas être exécuté, les dépendances ne sont pas chargées automatiquement. Si vous devez les examiner, vous devez les charger vous-même.

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Pour charger un assembly dans le contexte de chargement de réflexion uniquement

1. Utilisez la surcharge de méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> pour charger l’assembly d’après son nom complet, ou la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> pour charger l’assembly d’après son chemin. Si l’assembly est une image binaire, utilisez la surcharge de méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29>.

    > [!NOTE]
    > Vous ne pouvez pas utiliser le contexte de réflexion uniquement pour charger une version de mscorlib.dll à partir d’une version du .NET Framework autre que la version dans le contexte d’exécution.

2. Si l’assembly a des dépendances, la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ne les charge pas. Si vous devez les examiner, vous devez les charger vous-même.

3. Déterminez si un assembly est chargé dans le contexte de réflexion uniquement à l’aide de la propriété <xref:System.Reflection.Assembly.ReflectionOnly%2A> de l’assembly.

4. Si des attributs ont été appliqués à l’assembly ou à des types dans l’assembly, examinez ces attributs à l’aide de la classe <xref:System.Reflection.CustomAttributeData> pour vérifier qu’aucune tentative d’exécution du code dans le contexte de réflexion uniquement n’est effectuée. Utilisez la surcharge appropriée de la méthode <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> pour obtenir des objets <xref:System.Reflection.CustomAttributeData> représentant les attributs appliqués à un assembly, un membre, un module ou un paramètre.

    > [!NOTE]
    > Les attributs appliqués à l’assembly ou à son contenu peuvent être définis dans l’assembly, ou ils peuvent être définis dans un autre assembly chargé dans le contexte de réflexion uniquement. Il n’existe aucun moyen de savoir à l’avance où les attributs sont définis.

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment examiner les attributs appliqués à un assembly chargé dans le contexte de réflexion uniquement.

L’exemple de code définit un attribut personnalisé avec deux constructeurs et une propriété. L’attribut est appliqué à l’assembly, à un type déclaré dans l’assembly, à une méthode du type, et à un paramètre de la méthode. Lors de son exécution, l’assembly se charge dans le contexte de réflexion uniquement et affiche des informations sur les attributs personnalisés qui ont été appliqués sur lui-même et sur les types et membres qu’il contient.

> [!NOTE]
> Pour simplifier l’exemple de code, l’assembly se charge et s’examine lui-même. En règle générale, vous ne trouverez pas le même assembly chargé dans le contexte d’exécution et dans le contexte de réflexion uniquement.

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
