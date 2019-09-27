---
title: 'Guide pratique : créer des exceptions définies par l’utilisateur avec des messages d’exception localisés'
description: Découvrez comment créer des exceptions définies par l’utilisateur avec des messages d’exception localisés
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332990"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="49ec3-103">Guide pratique : créer des exceptions définies par l’utilisateur avec des messages d’exception localisés</span><span class="sxs-lookup"><span data-stu-id="49ec3-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="49ec3-104">Dans cet article, vous allez apprendre à créer des exceptions définies par l’utilisateur qui sont héritées de la classe de base <xref:System.Exception> avec des messages d’exception localisés à l’aide d’assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="49ec3-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="49ec3-105">Créer des exceptions personnalisées</span><span class="sxs-lookup"><span data-stu-id="49ec3-105">Create custom exceptions</span></span>

<span data-ttu-id="49ec3-106">.NET contient de nombreuses exceptions que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="49ec3-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="49ec3-107">Toutefois, dans certains cas, si aucune d’entre elles ne répond à vos besoins, vous pouvez créer vos propres exceptions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="49ec3-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="49ec3-108">Supposons que vous souhaitiez créer un `StudentNotFoundException` qui contient une propriété `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="49ec3-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="49ec3-109">Pour créer une exception personnalisée, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="49ec3-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="49ec3-110">Créez une classe sérialisable qui hérite de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="49ec3-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="49ec3-111">Le nom de la classe doit se terminer par « exception » :</span><span class="sxs-lookup"><span data-stu-id="49ec3-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="49ec3-112">Ajoutez les constructeurs par défaut :</span><span class="sxs-lookup"><span data-stu-id="49ec3-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="49ec3-113">Définissez les propriétés et constructeurs supplémentaires suivants :</span><span class="sxs-lookup"><span data-stu-id="49ec3-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="49ec3-114">Créer des messages d’exception localisés</span><span class="sxs-lookup"><span data-stu-id="49ec3-114">Create localized exception messages</span></span>

<span data-ttu-id="49ec3-115">Vous avez créé une exception personnalisée et vous pouvez la lever n’importe où avec du code similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="49ec3-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="49ec3-116">Le problème avec la ligne précédente est le suivant : « le Student est introuvable ».</span><span class="sxs-lookup"><span data-stu-id="49ec3-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="49ec3-117">est simplement une chaîne constante.</span><span class="sxs-lookup"><span data-stu-id="49ec3-117">is just a constant string.</span></span> <span data-ttu-id="49ec3-118">Dans une application localisée, vous souhaitez avoir des messages différents en fonction de la culture de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="49ec3-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="49ec3-119">Les [assemblys satellites](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) sont un bon moyen de le faire.</span><span class="sxs-lookup"><span data-stu-id="49ec3-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="49ec3-120">Un assembly satellite est un fichier. dll qui contient des ressources pour une langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="49ec3-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="49ec3-121">Lorsque vous demandez des ressources spécifiques au moment de l’exécution, le CLR trouve cette ressource en fonction de la culture de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="49ec3-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="49ec3-122">Si aucun assembly satellite n’est trouvé pour cette culture, les ressources de la culture par défaut sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="49ec3-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="49ec3-123">Pour créer les messages d’exception localisés :</span><span class="sxs-lookup"><span data-stu-id="49ec3-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="49ec3-124">Créez un dossier nommé *Resources* pour contenir les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="49ec3-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="49ec3-125">Ajoutez-lui un nouveau fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="49ec3-125">Add a new resource file to it.</span></span> <span data-ttu-id="49ec3-126">Pour ce faire, dans Visual Studio, cliquez avec le bouton droit sur le dossier dans **Explorateur de solutions**, puis sélectionnez **Ajouter** -> **nouveau élément** -> **ressources**.</span><span class="sxs-lookup"><span data-stu-id="49ec3-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="49ec3-127">Nommez le fichier *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="49ec3-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="49ec3-128">Il s’agit du fichier de ressources par défaut.</span><span class="sxs-lookup"><span data-stu-id="49ec3-128">This is the default resources file.</span></span>
1. <span data-ttu-id="49ec3-129">Ajoutez une paire nom/valeur pour votre message d’exception, comme dans l’illustration suivante : ![Add les ressources à la culture par défaut @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="49ec3-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="49ec3-130">Ajoutez un nouveau fichier de ressources pour le français.</span><span class="sxs-lookup"><span data-stu-id="49ec3-130">Add a new resource file for French.</span></span> <span data-ttu-id="49ec3-131">Nommez-le *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="49ec3-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="49ec3-132">Ajoutez une nouvelle paire nom/valeur pour le message d’exception, mais avec une valeur en français : ![Add les ressources à la culture fr-FR @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="49ec3-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="49ec3-133">Une fois le projet généré, le dossier de sortie de la génération doit contenir le dossier *fr-fr* avec un fichier *. dll* , qui est l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="49ec3-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="49ec3-134">Vous levez l’exception à l’aide d’un code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="49ec3-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="49ec3-135">Si le nom du projet est `TestProject` et que le fichier de ressources *ExceptionMessages. resx* se trouve dans le dossier *ressources* du projet, le nom complet du fichier de ressources est `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="49ec3-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="49ec3-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49ec3-136">See also</span></span>

- [<span data-ttu-id="49ec3-137">Comment créer des exceptions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="49ec3-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="49ec3-138">Création d’assemblys satellites pour les applications de bureau</span><span class="sxs-lookup"><span data-stu-id="49ec3-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="49ec3-139">base (C# référence)</span><span class="sxs-lookup"><span data-stu-id="49ec3-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="49ec3-140">This (C# référence)</span><span class="sxs-lookup"><span data-stu-id="49ec3-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
