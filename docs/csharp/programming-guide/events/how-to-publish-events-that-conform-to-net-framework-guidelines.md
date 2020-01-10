---
title: Comment publier des événements conformes aux instructions de .NET Framework- C# Guide de programmation
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 0ae240d0c078b5eaa690f128c037ee2471325872
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705338"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Comment publier des événements conformes aux instructions .NET Framework (C# Guide de programmation)
La procédure suivante montre comment ajouter à vos classes et structs des événements qui respectent le modèle .NET Framework standard. Tous les événements de la bibliothèque de classes .NET Framework sont basés sur le délégué <xref:System.EventHandler>, qui est défini comme suit :  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> .NET Framework 2.0 comprend une version générique de ce délégué : <xref:System.EventHandler%601>. Les exemples suivants montrent comment utiliser les deux versions.  
  
 Bien que les événements des classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser les événements sur le modèle .NET Framework à l’aide de <xref:System.EventHandler>, comme illustré dans l’exemple suivant.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Pour publier des événements basés sur le modèle EventHandler  
  
1. (Ignorez cette étape et passez à l’étape 3A si vous n’avez pas besoin d’envoyer des données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées au niveau d’une étendue qui est visible à la fois pour vos classes de serveur de publication et d’abonné. Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées. Dans cet exemple, une simple chaîne est retournée.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2. (Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601>.) Déclarez un délégué dans votre classe de publication. Donnez-lui un nom qui se termine par *EventHandler*. Le deuxième paramètre spécifie votre type EventArgs personnalisé.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
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
- [Guide de programmation C#](../index.md)
- [Événements](./index.md)
- [Délégués](../delegates/index.md)
