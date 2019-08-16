---
title: 'Gestion des ressources: Mot clé use'
description: En savoir plus F# sur le mot clé «use» et la fonction «using», qui peuvent contrôler l’initialisation et la libération des ressources.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627256"
---
# <a name="resource-management-the-use-keyword"></a>Gestion des ressources: Mot clé use

Cette rubrique décrit le mot `use` clé et `using` la fonction, qui peuvent contrôler l’initialisation et la libération des ressources.

## <a name="resources"></a>Ressources

Le terme *ressource* est utilisé de plusieurs façons. Oui, les ressources peuvent être des données utilisées par une application, telles que des chaînes, des graphiques et autres, mais dans ce contexte, les *ressources* font référence aux ressources logicielles ou du système d’exploitation, telles que les contextes de périphérique graphique, les descripteurs de fichiers, le réseau et la base de données. connexions, objets de concurrence tels que les handles d’attente, etc. L’utilisation de ces ressources par les applications implique l’acquisition de la ressource du système d’exploitation ou d’un autre fournisseur de ressources, puis la publication ultérieure de la ressource dans le pool pour qu’elle puisse être fournie à une autre application. Des problèmes se produisent lorsque les applications ne libèrent pas de ressources dans le pool commun.

## <a name="managing-resources"></a>Gestion des ressources

Pour gérer efficacement et de façon responsable les ressources dans une application, vous devez libérer les ressources rapidement et de manière prévisible. La .NET Framework vous aide à effectuer cette opération en `System.IDisposable` fournissant l’interface. Un type qui implémente `System.IDisposable` a la `System.IDisposable.Dispose` méthode, qui libère correctement les ressources. Les applications bien écrites garantissent `System.IDisposable.Dispose` que est appelée rapidement lorsqu’un objet qui contient une ressource limitée n’est plus nécessaire. Heureusement, la plupart des langages .NET offrent une prise en charge F# pour faciliter cette tâche et n’est pas une exception. Il existe deux constructions de langage utiles qui prennent en charge le modèle de `use` suppression: la `using` liaison et la fonction.

## <a name="use-binding"></a>utiliser la liaison

Le `use` mot clé a un formulaire qui ressemble à celui de `let` la liaison:

utiliser une*expression* de *valeur* = 

Il fournit les mêmes fonctionnalités qu’une `let` liaison, mais ajoute un appel `Dispose` à sur la valeur lorsque la valeur est hors de portée. Notez que le compilateur insère un contrôle null sur la valeur, de sorte que si la valeur est `null`, l’appel à `Dispose` n’est pas tenté.

L’exemple suivant montre comment fermer un fichier automatiquement à l’aide du `use` mot clé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Vous pouvez utiliser `use` dans les expressions de calcul, auquel cas une version personnalisée de l' `use` expression est utilisée. Pour plus d’informations, consultez [séquences](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md) et [expressions de calcul](computation-expressions.md).

## <a name="using-function"></a>utilisation de la fonction

La `using` fonction se présente sous la forme suivante:

`using`(*expression1*) *Function-or-lambda*

Dans une `using` expression, *expression1* crée l’objet qui doit être supprimé. Le résultat de *expression1* (l’objet qui doit être supprimé) devient un argument, *value*, à *Function-or-lambda*, qui est soit une fonction qui attend un seul argument restant d’un type qui correspond à la valeur produite par  *expression1*, ou une expression lambda qui attend un argument de ce type. À la fin de l’exécution de la fonction, le runtime appelle `Dispose` et libère les ressources (sauf si la valeur est `null`, auquel cas l’appel à dispose n’est pas tenté).

L’exemple suivant illustre l' `using` expression avec une expression lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

L’exemple suivant montre l' `using` expression avec une fonction.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Notez que la fonction peut être une fonction à laquelle des arguments ont déjà été appliqués. L'exemple de code suivant illustre cette tâche. Il crée un fichier qui contient la chaîne `XYZ`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

La `using` fonction et la `use` liaison sont des méthodes quasiment équivalentes pour accomplir la même chose. Le `using` mot clé fournit davantage de contrôle `Dispose` sur le moment où est appelé. Quand vous utilisez `using`, `Dispose` est appelé à la fin de la fonction ou de l’expression lambda; quand vous `use` utilisez le `Dispose` mot clé, est appelé à la fin du bloc de code conteneur. En général, il est préférable d’utiliser `use` à la place `using` de la fonction.

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
