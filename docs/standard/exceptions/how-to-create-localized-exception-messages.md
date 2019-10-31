---
title: 'Guide pratique : créer des exceptions définies par l’utilisateur avec des messages d’exception localisés'
description: Découvrez comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
author: Youssef1313
ms.date: 09/13/2019
ms.openlocfilehash: 453e332541628770932da2a6802fdcaee5211a84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141525"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Guide pratique : créer des exceptions définies par l’utilisateur avec des messages d’exception localisés

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

## <a name="create-localized-exception-messages"></a>Créer des messages d’exception localisés

Vous avez créé une exception personnalisée et vous pouvez la lever n’importe où avec du code similaire à ce qui suit :

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
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

  > [!NOTE]
  > Si le nom du projet est `TestProject` et que le fichier de ressources *ExceptionMessages. resx* se trouve dans le dossier *ressources* du projet, le nom complet du fichier de ressources est `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Voir aussi

- [Comment créer des exceptions définies par l’utilisateur](how-to-create-user-defined-exceptions.md)
- [Création d’assemblys satellites pour les applications de bureau](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# référence)](../../csharp/language-reference/keywords/base.md)
- [This (C# référence)](../../csharp/language-reference/keywords/this.md)
