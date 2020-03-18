---
title: Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
description: Apprenez à créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160181"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés

Dans cet article, vous apprendrez comment créer des exceptions <xref:System.Exception> définies par l’utilisateur qui sont héritées de la classe de base avec des messages d’exception localisés à l’aide d’assemblages satellites.

## <a name="create-custom-exceptions"></a>Créer des exceptions personnalisées

.NET contient de nombreuses exceptions différentes que vous pouvez utiliser. Cependant, dans certains cas, lorsqu’aucun d’entre eux ne répond à vos besoins, vous pouvez créer vos propres exceptions personnalisées.

Supposons que vous voulez `StudentNotFoundException` créer un `StudentName` qui contient une propriété.
Pour créer une exception personnalisée, suivez ces étapes :

1. Créez une classe sérialisable <xref:System.Exception>qui hérite de . Le nom de la classe doit se terminer par «Exception»:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. Ajouter les constructeurs par défaut :

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. Définir les propriétés et les constructeurs supplémentaires :

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a>Créer des messages d’exception localisés

Vous avez créé une exception personnalisée, et vous pouvez le jeter n’importe où avec le code comme ce qui suit:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Le problème avec la `"The student cannot be found."` ligne précédente est que c’est juste une chaîne constante. Dans une application localisée, vous souhaitez avoir des messages différents selon la culture de l’utilisateur.
[Les assemblages par satellite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) sont un bon moyen de le faire. Un assemblage satellite est un .dll qui contient des ressources pour une langue spécifique. Lorsque vous demandez une ressource spécifique au moment de l’exécution, le CLR trouve cette ressource en fonction de la culture de l’utilisateur. Si aucune assemblage par satellite n’est trouvée pour cette culture, les ressources de la culture par défaut sont utilisées.

Pour créer les messages d’exception localisés :

1. Créez un nouveau dossier nommé *Ressources* pour tenir les fichiers de ressources.
1. Ajoutez un nouveau fichier de ressources. Pour ce faire dans Visual Studio, cliquez à droite sur le dossier dans **Solution Explorer**, et **sélectionnez Ajouter** > de nouveaux**fichiers ressources****d’objets** > . Nommez le fichier *ExceptionMessages.resx*. Il s’agit du fichier des ressources par défaut.
1. Ajoutez une paire de nom/valeur pour votre message d’exception, comme l’image suivante montre :

   ![Ajouter des ressources à la culture par défaut](media/add-resources-to-default-culture.jpg)

1. Ajouter un nouveau fichier de ressources pour Français. *Nommez-le ExceptionMessages.fr-FR.resx*.
1. Ajoutez une paire de nom/valeur pour le message d’exception à nouveau, mais avec une valeur Français:

   ![Ajouter des ressources à la culture fr-FR](media/add-resources-to-fr-culture.jpg)

1. Après avoir construit le projet, le dossier de sortie de construction doit contenir le dossier *fr-FR* avec un fichier *.dll,* qui est l’assemblage satellite.
1. Vous jetez l’exception avec le code comme ce qui suit:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Si le nom `TestProject` du projet est et le fichier de ressources *ExceptionMessages.resx* réside dans le `TestProject.Resources.ExceptionMessages`dossier *Ressources* du projet, le nom entièrement qualifié du fichier de ressources est .

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des exceptions définies par l’utilisateur](how-to-create-user-defined-exceptions.md)
- [Création d'assemblys satellites pour les applications bureautiques](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (référence C#)](../../csharp/language-reference/keywords/base.md)
- [this (référence C#)](../../csharp/language-reference/keywords/this.md)
