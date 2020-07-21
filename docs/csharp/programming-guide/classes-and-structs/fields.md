---
title: Champs - Guide de programmation C#
description: Un champ en C# est une variable de tout type déclaré directement dans une classe ou un struct. Les champs sont membres de leur type contenant.
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 9bd2e198cd623788a21d4da73e89851a6d77e3bb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474785"
---
# <a name="fields-c-programming-guide"></a>Champs (Guide de programmation C#)

Un *champ* est une variable de tout type qui est déclarée directement dans une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md). Les champs sont *membres* de leur type contenant.

Une classe ou un struct peut avoir des champs d’instance, des champs statiques, ou les deux. Les champs d’instance sont spécifiques à une instance de type. Si vous avez une classe T avec un champ d’instance F, vous pouvez créer deux objets de type T et modifier la valeur de F dans chaque objet, sans affecter la valeur de l’autre objet. En revanche, un champ statique appartient à la classe, et il est partagé entre toutes les instances de cette classe. Vous pouvez accéder au champ statique uniquement à l’aide du nom de la classe. Si vous accédez au champ static par un nom d’instance, vous recevez une erreur de compilation [CS0176](../../misc/cs0176.md) .

En règle générale, vous devez utiliser des champs uniquement pour les variables dont l’accessibilité est privée ou protégée. Les données que votre classe expose au code client doivent être fournies par le biais de [méthodes](./methods.md), de [Propriétés](./properties.md)et d' [indexeurs](../indexers/index.md). L’utilisation de ces constructions pour l’accès indirect aux champs internes permet d’éviter les valeurs d’entrée non valides. Un champ privé qui stocke les données exposées par une propriété publique est appelé *magasin de stockage* ou *champ de stockage*.

En général, les champs stockent les données qui doivent être accessibles à plusieurs méthodes de classe et doivent être stockées plus longtemps que la durée de vie d’une méthode. Par exemple, une classe qui représente une date de calendrier peut avoir trois champs de type entier : un pour le mois, un pour le jour et un pour l’année. Les variables qui ne sont pas utilisées en dehors de la portée d’une méthode doivent être déclarées comme des *variables locales* dans le corps de la méthode.

Les champs sont déclarés dans le bloc Class en spécifiant le niveau d’accès du champ, suivi du type du champ, puis du nom du champ. Par exemple :

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Pour accéder à un champ dans un objet, ajoutez un point après le nom de l’objet, suivi du nom du champ, comme dans `objectname.fieldname`. Par exemple :

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Une valeur initiale peut être attribuée à un champ à l’aide de l’opérateur d’assignation, lorsque le champ est déclaré. Pour assigner automatiquement le champ `day` à `"Monday"`, par exemple, vous devez déclarer `day`, comme dans l’exemple suivant :

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Les champs sont initialisés juste avant le constructeur pour l’instance d’objet qui est appelée. Si le constructeur assigne la valeur d’un champ, la valeur assignée pendant la déclaration du champ sera remplacée. Pour plus d’informations, consultez [Utilisation de constructeurs](./using-constructors.md).

> [!NOTE]
> Un initialiseur de champ ne peut pas référencer d’autres champs d’instance.

Les champs peuvent être marqués comme [public](../../language-reference/keywords/public.md), [Private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [Internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md)ou [Private protected](../../language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder aux champs. Pour plus d’informations, consultez [Modificateurs d’accès](./access-modifiers.md).

Facultatif : vous pouvez déclarer un champ comme [static](../../language-reference/keywords/static.md). Ainsi, le champ est disponible à tout moment pour les appelants, même si aucune instance de la classe n’existe. Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](./static-classes-and-static-class-members.md).

Un champ peut être déclaré comme [readonly](../../language-reference/keywords/readonly.md). Un champ en lecture seule ne peut recevoir de valeur que pendant l’initialisation ou dans un constructeur. Un champ `static readonly` est très similaire à une constante, à ceci près que le compilateur C# n’a pas accès à la valeur d’un champ statique en lecture seule au moment de la compilation, mais seulement au moment de l’exécution. Pour plus d’informations, consultez [Constantes](./constants.md).

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Utilisation de constructeurs](./using-constructors.md)
- [Héritage](./inheritance.md)
- [Modificateurs d’accès](./access-modifiers.md)
- [Classes abstract et sealed et membres de classe](./abstract-and-sealed-classes-and-class-members.md)
