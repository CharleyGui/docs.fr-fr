---
title: Microsoft XML Serializer Generator
description: Vue d’ensemble de Microsoft XML Serializer Generator. Utilisez XML Serializer Generator afin de générer un assembly de sérialisation XML pour les types contenus dans votre projet.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c3f1fcda8a8a6abc58d35bf37e51485bb3590fa3
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794635"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="27211-104">Utilisation de Microsoft XML Serializer Generator sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="27211-105">Ce didacticiel montre comment utiliser Microsoft XML Serializer Generator dans une application C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27211-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="27211-106">Au cours de ce didacticiel, vous apprenez à :</span><span class="sxs-lookup"><span data-stu-id="27211-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="27211-107">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="27211-108">Ajouter une référence au package Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="27211-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="27211-109">Modifier votre fichier MyApp.csproj pour ajouter des dépendances</span><span class="sxs-lookup"><span data-stu-id="27211-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="27211-110">Ajouter une classe et un XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="27211-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="27211-111">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="27211-111">How to build and run the application</span></span>

<span data-ttu-id="27211-112">Comme l’outil [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est l’équivalent pour les projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="27211-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="27211-113">Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="27211-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27211-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="27211-114">Prerequisites</span></span>

<span data-ttu-id="27211-115">Pour suivre ce tutoriel :</span><span class="sxs-lookup"><span data-stu-id="27211-115">To complete this tutorial:</span></span>

- <span data-ttu-id="27211-116">[.Net Core 2,1 SDK](https://dotnet.microsoft.com/download) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="27211-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="27211-117">Votre éditeur de code favori.</span><span class="sxs-lookup"><span data-stu-id="27211-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="27211-118">Vous avez besoin d’installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="27211-118">Need to install a code editor?</span></span> <span data-ttu-id="27211-119">Essayez [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) !</span><span class="sxs-lookup"><span data-stu-id="27211-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="27211-120">Utiliser Microsoft XML Serializer Generator dans une application console .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="27211-121">Les instructions suivantes montrent comment utiliser XML Serializer Generator dans une application console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27211-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="27211-122">Créer une application console .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-122">Create a .NET Core console application</span></span>

<span data-ttu-id="27211-123">Ouvrez une invite de commandes et créez un dossier nommé *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="27211-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="27211-124">Accédez au dossier créé et tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="27211-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="27211-125">Ajouter une référence au package Microsoft.XmlSerializer.Generator dans le projet MyApp</span><span class="sxs-lookup"><span data-stu-id="27211-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="27211-126">Utilisez la [`dotnet add package`](../tools/dotnet-add-package.md) commande pour ajouter la référence dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="27211-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="27211-127">Tapez :</span><span class="sxs-lookup"><span data-stu-id="27211-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="27211-128">Vérifier les modifications apportées à MyApp.csproj après l’ajout du package</span><span class="sxs-lookup"><span data-stu-id="27211-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="27211-129">Ouvrez votre éditeur de code et c’est parti !</span><span class="sxs-lookup"><span data-stu-id="27211-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="27211-130">Nous travaillons encore à partir du répertoire *MyApp* dans lequel nous avons créé l’application.</span><span class="sxs-lookup"><span data-stu-id="27211-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="27211-131">Ouvrez *MyApp.csproj* dans votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="27211-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="27211-132">Après avoir exécuté [`dotnet add package`](../tools/dotnet-add-package.md) la commande, les lignes suivantes sont ajoutées à votre fichier projet *MyApp. csproj* :</span><span class="sxs-lookup"><span data-stu-id="27211-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="27211-133">Ajouter une autre section ItemGroup pour la prise en charge de l’outil d’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="27211-134">Ajoutez les lignes suivantes après la section `ItemGroup` que nous avons inspectée :</span><span class="sxs-lookup"><span data-stu-id="27211-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="27211-135">Ajouter une classe dans l’application</span><span class="sxs-lookup"><span data-stu-id="27211-135">Add a class in the application</span></span>

<span data-ttu-id="27211-136">Ouvrez *Program.cs* dans votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="27211-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="27211-137">Ajoutez la classe nommée *MyClass* dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="27211-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="27211-138">Créer un `XmlSerializer` pour MyClass</span><span class="sxs-lookup"><span data-stu-id="27211-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="27211-139">Ajoutez la ligne suivante à l’intérieur de *Main* pour créer un `XmlSerializer` pour MyClass :</span><span class="sxs-lookup"><span data-stu-id="27211-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="27211-140">Génération et exécution de l’application</span><span class="sxs-lookup"><span data-stu-id="27211-140">Build and run the application</span></span>

<span data-ttu-id="27211-141">Toujours dans le dossier *MyApp*, exécutez l’application avec [`dotnet run`](../tools/dotnet-run.md). Elle se charge automatiquement et utilise les sérialiseurs prégénérés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="27211-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="27211-142">Tapez la commande suivante dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="27211-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="27211-143">[`dotnet run`](../tools/dotnet-run.md)appelle [`dotnet build`](../tools/dotnet-build.md) pour s’assurer que les cibles de génération ont été générées, `dotnet <assembly.dll>` puis appelle pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="27211-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27211-144">Les commandes et les étapes indiquées dans ce didacticiel pour exécuter votre application sont utilisées uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="27211-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="27211-145">Une fois que vous êtes prêt à déployer votre application, consultez les différentes [stratégies de déploiement](../deploying/index.md) pour les applications .NET Core et la commande [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="27211-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="27211-146">Si tout fonctionne, un assembly nommé *MyApp.XmlSerializers.dll* est généré dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="27211-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="27211-147">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="27211-147">Congratulations!</span></span> <span data-ttu-id="27211-148">Vous venez de :</span><span class="sxs-lookup"><span data-stu-id="27211-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="27211-149">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="27211-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="27211-150">Ajouter une référence au package Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="27211-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="27211-151">Modifier votre fichier MyApp.csproj pour ajouter des dépendances</span><span class="sxs-lookup"><span data-stu-id="27211-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="27211-152">Ajouter une classe et un XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="27211-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="27211-153">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="27211-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="27211-154">Ressources associées</span><span class="sxs-lookup"><span data-stu-id="27211-154">Related resources</span></span>

- [<span data-ttu-id="27211-155">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="27211-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="27211-156">Comment sérialiser à l’aide de XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="27211-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="27211-157">Guide pratique pour sérialiser à l’aide de XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27211-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
