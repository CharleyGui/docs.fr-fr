---
title: Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
description: Découvrez comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160181"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés

Dans cet article, vous allez apprendre à créer des exceptions définies par l’utilisateur qui sont héritées de la classe de <xref:System.Exception> de base avec des messages d’exception localisés à l’aide d’assemblys satellites.

## <a name="create-custom-exceptions"></a>Créer des exceptions personnalisées

.NET contient de nombreuses exceptions que vous pouvez utiliser. Toutefois, dans certains cas, si aucune d’entre elles ne répond à vos besoins, vous pouvez créer vos propres exceptions personnalisées.

Supposons que vous souhaitiez créer un `StudentNotFoundException` qui contient une propriété `StudentName`.
Pour créer une exception personnalisée, procédez comme suit :

1. Créez une classe sérialisable qui hérite de <xref:System.Exception>. Le nom de la classe doit se terminer par « exception » :

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

1. Ajoutez les constructeurs par défaut :

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

1. Définissez les propriétés et constructeurs supplémentaires suivants :

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

Vous avez créé une exception personnalisée et vous pouvez la lever n’importe où avec du code similaire à ce qui suit :

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Le problème avec la ligne précédente est que `"The student cannot be found."` est simplement une chaîne constante. Dans une application localisée, vous souhaitez avoir des messages différents en fonction de la culture de l’utilisateur.
Les [assemblys satellites](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) sont un bon moyen de le faire. Un assembly satellite est un fichier. dll qui contient des ressources pour une langue spécifique. Lorsque vous demandez des ressources spécifiques au moment de l’exécution, le CLR trouve cette ressource en fonction de la culture de l’utilisateur. Si aucun assembly satellite n’est trouvé pour cette culture, les ressources de la culture par défaut sont utilisées.

Pour créer les messages d’exception localisés :

1. Créez un dossier nommé *Resources* pour contenir les fichiers de ressources.
1. Ajoutez-lui un nouveau fichier de ressources. Pour ce faire, dans Visual Studio, cliquez avec le bouton droit sur le dossier dans **Explorateur de solutions**, puis sélectionnez **Ajouter** > **nouvel élément** > **fichier de ressources**. Nommez le fichier *ExceptionMessages. resx*. Il s’agit du fichier de ressources par défaut.
1. Ajoutez une paire nom/valeur pour votre message d’exception, comme dans l’illustration suivante :

   ![Ajouter des ressources à la culture par défaut](media/add-resources-to-default-culture.jpg)

1. Ajoutez un nouveau fichier de ressources pour le français. Nommez-le *ExceptionMessages.fr-fr. resx*.
1. Ajoutez une nouvelle paire nom/valeur pour le message d’exception, mais avec une valeur en français :

   ![Ajouter des ressources à la culture fr-FR](media/add-resources-to-fr-culture.jpg)

1. Une fois le projet généré, le dossier de sortie de la génération doit contenir le dossier *fr-fr* avec un fichier *. dll* , qui est l’assembly satellite.
1. Vous levez l’exception à l’aide d’un code semblable au suivant :

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Si le nom du projet est `TestProject` et que le fichier de ressources *ExceptionMessages. resx* se trouve dans le dossier *ressources* du projet, le nom complet du fichier de ressources est `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Voir aussi

- [Comment créer des exceptions définies par l’utilisateur](how-to-create-user-defined-exceptions.md)
- [Création d’assemblys satellites pour les applications de bureau](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# référence)](../../csharp/language-reference/keywords/base.md)
- [This (C# référence)](../../csharp/language-reference/keywords/this.md)
