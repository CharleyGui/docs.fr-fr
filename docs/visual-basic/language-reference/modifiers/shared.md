---
title: Partagé
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: d8c9879ea2f62bfbeaa378d0aaee806623ea1c55
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579110"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)

Spécifie qu’un ou plusieurs éléments de programmation déclarés sont associés à une classe ou une structure au grand, et non à une instance spécifique de la classe ou de la structure.

## <a name="when-to-use-shared"></a>Quand utiliser le partagé

Le partage d’un membre d’une classe ou d’une structure le rend disponible pour chaque instance, plutôt que *non partagée*, où chaque instance conserve sa propre copie. Cela est utile, par exemple, si la valeur d’une variable s’applique à l’application entière. Si vous déclarez cette variable comme étant `Shared` , toutes les instances accèdent au même emplacement de stockage et si une instance modifie la valeur de la variable, toutes les instances accèdent à la valeur mise à jour.

Le partage ne modifie pas le niveau d’accès d’un membre. Par exemple, un membre de classe peut être partagé et privé (accessible uniquement à partir de la classe), ou non partagé et public. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Shared` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un `Shared` élément doit être une classe ou une structure, et ne peut pas être un fichier source, un espace de noms ou une procédure.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shared` avec [Overrides](overrides.md), [Overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md)ou [static](static.md) dans la même déclaration.

- **L’accès à.** Vous accédez à un élément Shared en le qualifiant avec son nom de classe ou de structure, et non avec le nom de variable d’une instance spécifique de sa classe ou structure. Vous n’avez même pas besoin de créer une instance d’une classe ou d’une structure pour accéder à ses membres partagés.

     L’exemple suivant appelle la procédure partagée <xref:System.Double.IsNaN%2A> exposée par la <xref:System.Double> structure.

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **Partage implicite.** Vous ne pouvez pas utiliser le `Shared` modificateur dans une [instruction Const](../statements/const-statement.md), mais les constantes sont partagées implicitement. De même, vous ne pouvez pas déclarer un membre d’un module ou une interface comme étant `Shared` , mais ils sont implicitement partagés.

## <a name="behavior"></a>Comportement

- **Rangement.** Une variable ou un événement partagé est stocké en mémoire une seule fois, quel que soit le nombre d’instances que vous créez de sa classe ou structure. De même, une procédure ou une propriété partagée ne contient qu’un seul jeu de variables locales.

- **Accès par le biais d’une variable d’instance.** Il est possible d’accéder à un élément Shared en le qualifiant avec le nom d’une variable qui contient une instance spécifique de sa classe ou structure. Bien que cela fonctionne généralement comme prévu, le compilateur génère un message d’avertissement et donne l’accès par le biais du nom de la classe ou de la structure au lieu de la variable.

- **Accès par le biais d’une expression d’instance.** Si vous accédez à un élément partagé par le biais d’une expression qui retourne une instance de sa classe ou structure, le compilateur effectue l’accès via le nom de la classe ou de la structure au lieu d’évaluer l’expression. Cela produit des résultats inattendus si vous avez souhaité que l’expression effectue d’autres actions et retourne l’instance. L'exemple suivant illustre ce comportement.
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     Dans l’exemple précédent, le compilateur génère un message d’avertissement à la fois que le code accède à la propriété partagée `Total` par le biais d’une instance. Dans chaque cas, il effectue l’accès directement par le biais de la classe `ShareTotal` et n’utilise aucune instance. Dans le cas de l’appel prévu à la procédure `ReturnClass` , cela signifie qu’elle ne génère même pas d’appel à `ReturnClass` , donc l’action supplémentaire d’affichage de « Function ReturnClass () called » n’est pas effectuée.

Le modificateur `Shared` peut être utilisé dans les contextes suivants :

- [Dim (instruction)](../statements/dim-statement.md)
- [Event, instruction](../statements/event-statement.md)
- [Function (instruction)](../statements/function-statement.md)
- [Operator Statement](../statements/operator-statement.md)
- [Property Statement](../statements/property-statement.md)
- [Sub (instruction)](../statements/sub-statement.md)
  
## <a name="see-also"></a>Voir aussi

- [Shadows](shadows.md)
- [Statique](static.md)
- [Durée de vie dans Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
