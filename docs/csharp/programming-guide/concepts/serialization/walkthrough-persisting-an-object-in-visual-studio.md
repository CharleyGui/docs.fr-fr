---
title: 'Procédure pas à pas : persistance d’un objet avec C#'
description: Cet exemple crée un objet Loan de base en C# et conserve ses données dans un fichier, puis crée un nouvel objet avec les données du fichier.
ms.date: 04/26/2018
ms.openlocfilehash: 9f165addc5b9b0d056936458e8529ec1912c417b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302761"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="591aa-103">Procédure pas à pas : Rendre un objet persistant avec C\#</span><span class="sxs-lookup"><span data-stu-id="591aa-103">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="591aa-104">Vous pouvez utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, ce qui vous permet de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="591aa-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="591aa-105">Dans cette procédure pas à pas, vous créez un objet `Loan` de base et vous stockez ses données dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="591aa-105">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="591aa-106">Vous récupérerez ensuite les données du fichier lors de la recréation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="591aa-106">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="591aa-107">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="591aa-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="591aa-108">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour le dossier.</span><span class="sxs-lookup"><span data-stu-id="591aa-108">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="591aa-109">Les autorisations sont définies à l’aide de listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="591aa-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="591aa-110">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, ce qui représente une autorisation inférieure.</span><span class="sxs-lookup"><span data-stu-id="591aa-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="591aa-111">Quand c’est possible, il est plus sûr de créer le fichier lors du déploiement et d’accorder l’autorisation `Read` sur un seul fichier (au lieu d’accorder l’autorisation Créer pour un dossier).</span><span class="sxs-lookup"><span data-stu-id="591aa-111">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="591aa-112">Par ailleurs, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.</span><span class="sxs-lookup"><span data-stu-id="591aa-112">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="591aa-113">Cet exemple stocke les données dans un fichier au format binaire.</span><span class="sxs-lookup"><span data-stu-id="591aa-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="591aa-114">Ces formats ne doivent pas être utilisés pour des données sensibles, telles que les mots de passe ou les informations relatives à la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="591aa-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="591aa-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="591aa-115">Prerequisites</span></span>

- <span data-ttu-id="591aa-116">Pour générer et exécuter, installez le [SDK .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="591aa-116">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="591aa-117">Installez votre éditeur de code favori, si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="591aa-117">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="591aa-118">Vous avez besoin d’installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="591aa-118">Need to install a code editor?</span></span> <span data-ttu-id="591aa-119">Essayez [Visual Studio](https://visualstudio.com/downloads) !</span><span class="sxs-lookup"><span data-stu-id="591aa-119">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="591aa-120">L’exemple exige C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="591aa-120">The example requires C# 7.3.</span></span> <span data-ttu-id="591aa-121">Voir [Sélectionner la version du langage C#](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="591aa-121">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="591aa-122">Vous pouvez examiner l’exemple de code en ligne [sur le référentiel GitHub des exemples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="591aa-122">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="591aa-123">Création de l’objet loan</span><span class="sxs-lookup"><span data-stu-id="591aa-123">Creating the loan object</span></span>

<span data-ttu-id="591aa-124">La première étape consiste à créer une classe `Loan` et une application console qui utilise cette classe :</span><span class="sxs-lookup"><span data-stu-id="591aa-124">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="591aa-125">Créez une application.</span><span class="sxs-lookup"><span data-stu-id="591aa-125">Create a new application.</span></span> <span data-ttu-id="591aa-126">Tapez `dotnet new console -o serialization` pour créer une application console dans un sous-répertoire nommé `serialization`.</span><span class="sxs-lookup"><span data-stu-id="591aa-126">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="591aa-127">Ouvrez l’application dans votre éditeur, et ajoutez une nouvelle classe nommée `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="591aa-127">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="591aa-128">Ajoutez le code suivant à la classe `Loan` :</span><span class="sxs-lookup"><span data-stu-id="591aa-128">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="591aa-129">Vous devez également créer une application simple qui utilise la classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="591aa-129">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="591aa-130">Sérialiser l’objet loan</span><span class="sxs-lookup"><span data-stu-id="591aa-130">Serialize the loan object</span></span>

1. <span data-ttu-id="591aa-131">Ouvrez `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="591aa-131">Open `Program.cs`.</span></span> <span data-ttu-id="591aa-132">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="591aa-132">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="591aa-133">Ajoutez un gestionnaire d’événements pour l’événement `PropertyChanged`, ainsi que quelques lignes pour modifier l’objet `Loan` et afficher les modifications.</span><span class="sxs-lookup"><span data-stu-id="591aa-133">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="591aa-134">Vous pouvez voir les ajouts dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="591aa-134">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="591aa-135">À ce stade, vous pouvez exécuter le code et voir la sortie actuelle :</span><span class="sxs-lookup"><span data-stu-id="591aa-135">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="591aa-136">L’exécution de cette application à plusieurs reprises écrit toujours les mêmes valeurs.</span><span class="sxs-lookup"><span data-stu-id="591aa-136">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="591aa-137">Un nouvel objet Loan est créé chaque fois que vous exécutez le programme.</span><span class="sxs-lookup"><span data-stu-id="591aa-137">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="591aa-138">Dans la réalité, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="591aa-138">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="591aa-139">Un code de sérialisation signifie que vous conservez le taux d’intérêt le plus récent entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="591aa-139">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="591aa-140">C’est ce que vous ferez à l’étape suivante, en ajoutant la sérialisation à la classe Loan.</span><span class="sxs-lookup"><span data-stu-id="591aa-140">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="591aa-141">Utilisation de la sérialisation pour rendre l’objet persistant</span><span class="sxs-lookup"><span data-stu-id="591aa-141">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="591aa-142">Pour rendre les valeurs de la classe Loan persistantes, vous devez d’abord marquer la classe avec l’attribut `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="591aa-142">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="591aa-143">Ajoutez le code suivant au-dessus de la déclaration de la classe Loan :</span><span class="sxs-lookup"><span data-stu-id="591aa-143">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="591aa-144"><xref:System.SerializableAttribute> indique au compilateur que tout ce que contient la classe peut être stocké dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="591aa-144">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="591aa-145">Étant donné que l’événement `PropertyChanged` ne représente pas une partie du graphe d’objets qui doit être stocké, il ne doit pas être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="591aa-145">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="591aa-146">Procéder ainsi sérialiserait tous les objets qui sont attachés à cet événement.</span><span class="sxs-lookup"><span data-stu-id="591aa-146">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="591aa-147">Vous pouvez ajouter <xref:System.NonSerializedAttribute> à la déclaration du champ pour le gestionnaire d’événements `PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="591aa-147">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="591aa-148">À compter de C# 7.3, vous pouvez attacher des attributs au champ de stockage d’une propriété implémentée automatiquement en utilisant la valeur cible `field`.</span><span class="sxs-lookup"><span data-stu-id="591aa-148">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="591aa-149">Le code suivant ajoute une propriété `TimeLastLoaded` et la marque comme non sérialisable :</span><span class="sxs-lookup"><span data-stu-id="591aa-149">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="591aa-150">L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp.</span><span class="sxs-lookup"><span data-stu-id="591aa-150">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="591aa-151">Pour sérialiser la classe et l’écrire dans un fichier, vous utilisez les espaces de noms <xref:System.IO> et <xref:System.Runtime.Serialization.Formatters.Binary>.</span><span class="sxs-lookup"><span data-stu-id="591aa-151">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="591aa-152">Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux espaces de noms nécessaires, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="591aa-152">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="591aa-153">L’étape suivante consiste à ajouter le code permettant de désérialiser l’objet à partir du fichier lors de la création de l’objet.</span><span class="sxs-lookup"><span data-stu-id="591aa-153">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="591aa-154">Ajoutez une constante à la classe pour le nom de fichier des données sérialisées, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="591aa-154">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="591aa-155">Ensuite, ajoutez le code suivant après la ligne qui crée l’objet `TestLoan` :</span><span class="sxs-lookup"><span data-stu-id="591aa-155">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="591aa-156">Vous devez d’abord vérifier que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="591aa-156">You first must check that the file exists.</span></span> <span data-ttu-id="591aa-157">S’il existe, créez une classe <xref:System.IO.Stream> pour lire le fichier binaire et une classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour convertir le fichier.</span><span class="sxs-lookup"><span data-stu-id="591aa-157">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="591aa-158">Vous devez également convertir le type de flux en type d’objet Loan.</span><span class="sxs-lookup"><span data-stu-id="591aa-158">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="591aa-159">Vous devez ensuite ajouter du code pour sérialiser la classe dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="591aa-159">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="591aa-160">Ajoutez le code suivant après le code existant de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="591aa-160">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="591aa-161">À ce stade, vous pouvez de nouveau générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="591aa-161">At this point, you can again build and run the application.</span></span> <span data-ttu-id="591aa-162">La première fois qu’elle s’exécute, notez que le taux d’intérêt commence à 7,5, puis qu’il passe à 7,1.</span><span class="sxs-lookup"><span data-stu-id="591aa-162">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="591aa-163">Fermez l’application et exécutez-la de nouveau.</span><span class="sxs-lookup"><span data-stu-id="591aa-163">Close the application and then run it again.</span></span> <span data-ttu-id="591aa-164">L’application indique maintenant qu’elle a lu le fichier enregistré, et le taux d’intérêt est de 7,1 même avant le code qui le change.</span><span class="sxs-lookup"><span data-stu-id="591aa-164">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="591aa-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="591aa-165">See also</span></span>

- [<span data-ttu-id="591aa-166">Sérialisation (C#)</span><span class="sxs-lookup"><span data-stu-id="591aa-166">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="591aa-167">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="591aa-167">C# Programming Guide</span></span>](../../index.md)
