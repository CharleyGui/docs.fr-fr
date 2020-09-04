---
title: Publier des événements conformes aux instructions .NET-Guide de programmation C#
description: Découvrez comment publier des événements conformes aux instructions .NET. Tous les événements de la bibliothèque de classes .NET sont basés sur le délégué EventHandler.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cc8b0a9fdaeeb6ab6290630c5d78044c2696b9a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466168"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a>Comment publier des événements conformes aux instructions .NET (Guide de programmation C#)

La procédure suivante montre comment ajouter des événements qui suivent le modèle .NET standard à vos classes et structures. Tous les événements de la bibliothèque de classes .NET sont basés sur le <xref:System.EventHandler> délégué, qui est défini comme suit :

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> .NET Framework 2,0 introduit une version générique de ce délégué, <xref:System.EventHandler%601> . Les exemples suivants montrent comment utiliser les deux versions.

Bien que les événements dans les classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser vos événements sur le modèle .NET à l’aide de <xref:System.EventHandler> , comme indiqué dans l’exemple suivant.

Le nom `EventHandler` peut entraîner un peu de confusion, car il ne gère pas réellement l’événement. Le <xref:System.EventHandler> générique et <xref:System.EventHandler%601> sont des types délégués. Une méthode ou une expression lambda dont la signature correspond à la définition de délégué est le *Gestionnaire d’événements* et sera appelée lorsque l’événement est déclenché.

## <a name="publish-events-based-on-the-eventhandler-pattern"></a>Publier des événements basés sur le modèle EventHandler

1. (Ignorez cette étape et passez à l’étape 3A si vous n’avez pas besoin d’envoyer des données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées au niveau d’une étendue qui est visible à la fois pour vos classes de serveur de publication et d’abonné. Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées. Dans cet exemple, une simple chaîne est retournée.

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. (Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601> .) Déclarez un délégué dans votre classe de publication. Donnez-lui un nom qui se termine par `EventHandler` . Le deuxième paramètre spécifie votre `EventArgs` type personnalisé.

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.

    1. Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique. Il est inutile de déclarer le délégué, car il l’est déjà dans l’espace de noms <xref:System> inclus au moment où vous créez votre projet C#. Ajoutez le code suivant à votre classe de serveur de publication.

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé. Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>Exemple

L’exemple suivant est une illustration des étapes précédentes avec l’utilisation d’une classe EventArgs personnalisée et de <xref:System.EventHandler%601> comme type d’événement.

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Delegate>
- [Guide de programmation C#](../index.md)
- [Événements](index.md)
- [Délégués](../delegates/index.md)
