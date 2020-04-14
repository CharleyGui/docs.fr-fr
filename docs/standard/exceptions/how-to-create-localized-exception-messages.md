---
title: Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
description: Apprenez à créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243347"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="d08fc-103">Comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés</span><span class="sxs-lookup"><span data-stu-id="d08fc-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="d08fc-104">Dans cet article, vous apprendrez comment créer des exceptions <xref:System.Exception> définies par l’utilisateur qui sont héritées de la classe de base avec des messages d’exception localisés à l’aide d’assemblages satellites.</span><span class="sxs-lookup"><span data-stu-id="d08fc-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="d08fc-105">Créer des exceptions personnalisées</span><span class="sxs-lookup"><span data-stu-id="d08fc-105">Create custom exceptions</span></span>

<span data-ttu-id="d08fc-106">.NET contient de nombreuses exceptions différentes que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="d08fc-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="d08fc-107">Cependant, dans certains cas, lorsqu’aucun d’entre eux ne répond à vos besoins, vous pouvez créer vos propres exceptions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d08fc-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="d08fc-108">Supposons que vous voulez `StudentNotFoundException` créer un `StudentName` qui contient une propriété.</span><span class="sxs-lookup"><span data-stu-id="d08fc-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="d08fc-109">Pour créer une exception personnalisée, suivez ces étapes :</span><span class="sxs-lookup"><span data-stu-id="d08fc-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="d08fc-110">Créez une classe sérialisable <xref:System.Exception>qui hérite de .</span><span class="sxs-lookup"><span data-stu-id="d08fc-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="d08fc-111">Le nom de la classe doit se terminer par «Exception»:</span><span class="sxs-lookup"><span data-stu-id="d08fc-111">The class name should end in "Exception":</span></span>

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

1. <span data-ttu-id="d08fc-112">Ajouter les constructeurs par défaut :</span><span class="sxs-lookup"><span data-stu-id="d08fc-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="d08fc-113">Définir les propriétés et les constructeurs supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="d08fc-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="d08fc-114">Créer des messages d’exception localisés</span><span class="sxs-lookup"><span data-stu-id="d08fc-114">Create localized exception messages</span></span>

<span data-ttu-id="d08fc-115">Vous avez créé une exception personnalisée, et vous pouvez le jeter n’importe où avec le code comme ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="d08fc-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="d08fc-116">Le problème avec la `"The student cannot be found."` ligne précédente est que c’est juste une chaîne constante.</span><span class="sxs-lookup"><span data-stu-id="d08fc-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="d08fc-117">Dans une application localisée, vous souhaitez avoir des messages différents selon la culture de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d08fc-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="d08fc-118">[Les assemblages par satellite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) sont un bon moyen de le faire.</span><span class="sxs-lookup"><span data-stu-id="d08fc-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="d08fc-119">Un assemblage satellite est un .dll qui contient des ressources pour une langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="d08fc-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="d08fc-120">Lorsque vous demandez une ressource spécifique au moment de l’exécution, le CLR trouve cette ressource en fonction de la culture de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d08fc-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="d08fc-121">Si aucune assemblage par satellite n’est trouvée pour cette culture, les ressources de la culture par défaut sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="d08fc-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="d08fc-122">Pour créer les messages d’exception localisés :</span><span class="sxs-lookup"><span data-stu-id="d08fc-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="d08fc-123">Créez un nouveau dossier nommé *Ressources* pour tenir les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="d08fc-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="d08fc-124">Ajoutez un nouveau fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="d08fc-124">Add a new resource file to it.</span></span> <span data-ttu-id="d08fc-125">Pour ce faire dans Visual Studio, cliquez à droite sur le dossier dans **Solution Explorer**, et **sélectionnez Ajouter** > de nouveaux**fichiers ressources\*\*\*\*d’objets** > .</span><span class="sxs-lookup"><span data-stu-id="d08fc-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="d08fc-126">Nommez le fichier *ExceptionMessages.resx*.</span><span class="sxs-lookup"><span data-stu-id="d08fc-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="d08fc-127">Il s’agit du fichier des ressources par défaut.</span><span class="sxs-lookup"><span data-stu-id="d08fc-127">This is the default resources file.</span></span>
1. <span data-ttu-id="d08fc-128">Ajoutez une paire de nom/valeur pour votre message d’exception, comme l’image suivante montre :</span><span class="sxs-lookup"><span data-stu-id="d08fc-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Ajouter des ressources à la culture par défaut](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="d08fc-130">Ajouter un nouveau fichier de ressources pour Français.</span><span class="sxs-lookup"><span data-stu-id="d08fc-130">Add a new resource file for French.</span></span> <span data-ttu-id="d08fc-131">*Nommez-le ExceptionMessages.fr-FR.resx*.</span><span class="sxs-lookup"><span data-stu-id="d08fc-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="d08fc-132">Ajoutez une paire de nom/valeur pour le message d’exception à nouveau, mais avec une valeur Français:</span><span class="sxs-lookup"><span data-stu-id="d08fc-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Ajouter des ressources à la culture fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="d08fc-134">Après avoir construit le projet, le dossier de sortie de construction doit contenir le dossier *fr-FR* avec un fichier *.dll,* qui est l’assemblage satellite.</span><span class="sxs-lookup"><span data-stu-id="d08fc-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="d08fc-135">Vous jetez l’exception avec le code comme ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="d08fc-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="d08fc-136">Si le nom `TestProject` du projet est et le fichier de ressources *ExceptionMessages.resx* réside dans le `TestProject.Resources.ExceptionMessages`dossier *Ressources* du projet, le nom entièrement qualifié du fichier de ressources est .</span><span class="sxs-lookup"><span data-stu-id="d08fc-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d08fc-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d08fc-137">See also</span></span>

- [<span data-ttu-id="d08fc-138">Guide pratique pour créer des exceptions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d08fc-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="d08fc-139">Création d'assemblys satellites pour les applications bureautiques</span><span class="sxs-lookup"><span data-stu-id="d08fc-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="d08fc-140">base (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d08fc-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="d08fc-141">this (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d08fc-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
