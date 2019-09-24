---
title: Concevoir avec des types référence Nullable
description: Ce tutoriel avancé présente les types référence Nullable. Il explique comment exprimer une intention de conception lorsque les valeurs de référence peuvent être Null et comment, dans le cas contraire, indiquer au compilateur qu’elles ne peuvent pas être Null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: ea8059061dccc85060b4f6244ff0d7be9b7708b8
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214417"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="29c24-104">Tutoriel : Exprimer plus clairement une intention de conception avec les types référence Nullable et non Nullable</span><span class="sxs-lookup"><span data-stu-id="29c24-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="29c24-105">C# 8 introduit les **types référence Nullable**, qui viennent compléter les types référence de la même façon que les types valeur Nullable complètent les types valeur.</span><span class="sxs-lookup"><span data-stu-id="29c24-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="29c24-106">Pour déclarer une variable comme étant un **type référence Nullable**, on ajoute `?` au type.</span><span class="sxs-lookup"><span data-stu-id="29c24-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="29c24-107">Par exemple, `string?` représente une `string` Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="29c24-108">Vous pouvez utiliser ces nouveaux types pour exprimer plus clairement votre intention de conception : certaines variables *doivent toujours avoir une valeur*, d’autres *peuvent ne pas en avoir*.</span><span class="sxs-lookup"><span data-stu-id="29c24-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="29c24-109">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="29c24-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="29c24-110">incorporer des types référence Nullable et non Nullable dans vos conceptions ;</span><span class="sxs-lookup"><span data-stu-id="29c24-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="29c24-111">activer les contrôles de type référence Nullable dans l’ensemble de votre code ;</span><span class="sxs-lookup"><span data-stu-id="29c24-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="29c24-112">écrire du code permettant au compilateur d’appliquer ces décisions de conception ;</span><span class="sxs-lookup"><span data-stu-id="29c24-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="29c24-113">utiliser la fonctionnalité de référence Nullable dans vos propres conceptions.</span><span class="sxs-lookup"><span data-stu-id="29c24-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29c24-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="29c24-114">Prerequisites</span></span>

<span data-ttu-id="29c24-115">Vous devrez configurer votre ordinateur de façon à exécuter .NET Core, avec le compilateur C# 8.0 bêta.</span><span class="sxs-lookup"><span data-stu-id="29c24-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="29c24-116">Le C# compilateur 8 bêta est disponible avec [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou [.net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="29c24-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="29c24-117">Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29c24-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="29c24-118">Incorporer des types référence Nullable dans des conceptions</span><span class="sxs-lookup"><span data-stu-id="29c24-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="29c24-119">Dans ce tutoriel, vous allez générer une bibliothèque qui modélise la réalisation d’une enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="29c24-120">Le code utilise des types référence Nullable et non Nullable pour représenter les concepts du monde réel.</span><span class="sxs-lookup"><span data-stu-id="29c24-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="29c24-121">Les questions de l’enquête ne peuvent jamais être Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-121">The survey questions can never be null.</span></span> <span data-ttu-id="29c24-122">Si la personne interrogée ne souhaite pas répondre à une question,</span><span class="sxs-lookup"><span data-stu-id="29c24-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="29c24-123">la réponse est Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-123">The responses might be null in this case.</span></span>

<span data-ttu-id="29c24-124">Le code que vous allez écrire pour cet exemple exprime cette intention, que le compilateur se charge d’appliquer.</span><span class="sxs-lookup"><span data-stu-id="29c24-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="29c24-125">Créer l’application et activer les types référence Nullable</span><span class="sxs-lookup"><span data-stu-id="29c24-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="29c24-126">Créez une application console dans Visual Studio ou en ligne de commande avec `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="29c24-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="29c24-127">Nommez l'application `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="29c24-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="29c24-128">Une fois l’application créée, activez les fonctionnalités de la version C# 8 bêta.</span><span class="sxs-lookup"><span data-stu-id="29c24-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="29c24-129">Ouvrez le fichier `csproj` et ajoutez un élément `LangVersion` à l'élément `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="29c24-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="29c24-130">Vous devez cocher la fonctionnalité **Types référence Nullable**, même dans les projets C# 8.</span><span class="sxs-lookup"><span data-stu-id="29c24-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="29c24-131">En effet, une fois la fonctionnalité activée, les déclarations de variables référence existantes deviennent des **types référence non Nullable**.</span><span class="sxs-lookup"><span data-stu-id="29c24-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="29c24-132">Bien que cette décision aide à identifier les problèmes de contrôle de type Null dans le code, elle ne reflète pas forcément l’intention de conception d’origine.</span><span class="sxs-lookup"><span data-stu-id="29c24-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="29c24-133">Activez la fonctionnalité en définissant l’élément `Nullable` sur `enable` :</span><span class="sxs-lookup"><span data-stu-id="29c24-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> <span data-ttu-id="29c24-134">L’élément `Nullable` était nommé `NullableContextOptions`.</span><span class="sxs-lookup"><span data-stu-id="29c24-134">The `Nullable` element was previously named `NullableContextOptions`.</span></span> <span data-ttu-id="29c24-135">Les navires renommés avec Visual Studio 2019, 16.2-p1.</span><span class="sxs-lookup"><span data-stu-id="29c24-135">The rename ships with Visual Studio 2019, 16.2-p1.</span></span> <span data-ttu-id="29c24-136">Le kit SDK .NET Core 3.0.100-preview5-011568 n’a pas cette modification.</span><span class="sxs-lookup"><span data-stu-id="29c24-136">The .NET Core SDK 3.0.100-preview5-011568 does not have this change.</span></span> <span data-ttu-id="29c24-137">Si vous utilisez le CLI .NET Core, vous devrez utiliser `NullableContextOptions` jusqu'à ce que la préversion suivante soit disponible.</span><span class="sxs-lookup"><span data-stu-id="29c24-137">If you are using the .NET Core CLI, you'll need to use `NullableContextOptions` until the next preview is available.</span></span>

> [!NOTE]
> <span data-ttu-id="29c24-138">Lorsque C# 8 est publié (pas en préversion), l’élément `Nullable` est ajouté par les nouveaux modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="29c24-138">When C# 8 is released (not in preview mode), the `Nullable` element will be added by new project templates.</span></span> <span data-ttu-id="29c24-139">En attendant, vous devrez l’ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="29c24-139">Until then, you'll need to add it manually.</span></span>

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="29c24-140">Concevoir les types de l’application</span><span class="sxs-lookup"><span data-stu-id="29c24-140">Design the types for the application</span></span>

<span data-ttu-id="29c24-141">Cette application d’enquête implique la création d’un certain nombre de classes :</span><span class="sxs-lookup"><span data-stu-id="29c24-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="29c24-142">une classe qui modélise la liste des questions ;</span><span class="sxs-lookup"><span data-stu-id="29c24-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="29c24-143">une classe qui modélise la liste des personnes contactées pour l’enquête ;</span><span class="sxs-lookup"><span data-stu-id="29c24-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="29c24-144">une classe qui modélise les réponses d’une personne ayant répondu à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="29c24-145">Ces types utilisent des types référence Nullable et non Nullable pour indiquer quels membres sont requis et lesquels sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="29c24-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="29c24-146">Les types référence Nullable communiquent clairement cette intention de conception :</span><span class="sxs-lookup"><span data-stu-id="29c24-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="29c24-147">Les questions qui font partie de l’enquête ne peuvent jamais être Null : poser une question vide n’aurait pas de sens.</span><span class="sxs-lookup"><span data-stu-id="29c24-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="29c24-148">Les personnes interrogées ne peuvent jamais être Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-148">The respondents can never be null.</span></span> <span data-ttu-id="29c24-149">Vous souhaitez faire un suivi des personnes que vous avez contactées, même de celles qui ont refusé de participer.</span><span class="sxs-lookup"><span data-stu-id="29c24-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="29c24-150">La réponse à une question peut être Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-150">Any response to a question may be null.</span></span> <span data-ttu-id="29c24-151">Les personnes interrogées peuvent refuser de répondre à certaines questions ou à la totalité d’entre elles.</span><span class="sxs-lookup"><span data-stu-id="29c24-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="29c24-152">Si vous avez déjà programmé en C#, vous avez peut-être une telle habitude des types référence qui autorisent les valeurs Null que vous avez raté certaines occasions de déclarer des instances non Nullable :</span><span class="sxs-lookup"><span data-stu-id="29c24-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="29c24-153">La collection de questions doit être non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="29c24-154">La collection de personnes interrogées doit être non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="29c24-155">En écrivant le code, vous allez voir qu’utiliser par défaut un type référence non Nullable pour les références permet d’éviter des erreurs courantes susceptibles d’aboutir à des exceptions de référence Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="29c24-156">Ce tutoriel vous aide à prendre des décisions sur les variables qui peuvent ou non être Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="29c24-157">Avant, le langage ne fournissait pas de syntaxe permettant d’exprimer ces décisions ;</span><span class="sxs-lookup"><span data-stu-id="29c24-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="29c24-158">maintenant, si.</span><span class="sxs-lookup"><span data-stu-id="29c24-158">Now it does.</span></span>

<span data-ttu-id="29c24-159">L’application que vous allez créer effectuera les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="29c24-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="29c24-160">Créer une enquête et y ajouter des questions.</span><span class="sxs-lookup"><span data-stu-id="29c24-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="29c24-161">Créer un ensemble pseudo-aléatoire de personnes interrogées pour l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="29c24-162">Contacter les personnes interrogées jusqu'à ce que la taille de l’enquête réalisée atteigne le nombre visé.</span><span class="sxs-lookup"><span data-stu-id="29c24-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="29c24-163">Écrire des statistiques importantes sur les réponses à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="29c24-164">Créer l’enquête avec des types Nullable et non Nullable</span><span class="sxs-lookup"><span data-stu-id="29c24-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="29c24-165">La première partie du code crée l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="29c24-166">Vous allez écrire des classes pour modéliser une question et une enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="29c24-167">L’enquête comporte trois types de questions, en fonction du format de la réponse : réponses par oui ou non, réponses chiffrées et réponses textuelles.</span><span class="sxs-lookup"><span data-stu-id="29c24-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="29c24-168">Créez une classe `public` `SurveyQuestion` :</span><span class="sxs-lookup"><span data-stu-id="29c24-168">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="29c24-169">Le compilateur interprète chaque déclaration de variable de type référence comme **non Nullable** pour le code dans un contexte nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-169">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="29c24-170">Un premier avertissement apparaît lorsque l’on ajoute des propriétés pour le texte et le type de la question avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="29c24-170">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="29c24-171">Comme `QuestionText` n’est pas initialisé, le compilateur émet l’avertissement selon lequel une propriété non Nullable n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="29c24-171">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="29c24-172">Or, la conception exige que le texte de la question soit non Null. Ajoutez un constructeur pour l’initialiser, ainsi que la valeur `QuestionType`.</span><span class="sxs-lookup"><span data-stu-id="29c24-172">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="29c24-173">Une fois terminée, la définition de classe se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="29c24-173">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="29c24-174">Le fait d’ajouter le constructeur supprime l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="29c24-174">Adding the constructor removes the warning.</span></span> <span data-ttu-id="29c24-175">L’argument du constructeur étant également un type référence non Nullable, le compilateur ne génère pas d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="29c24-175">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="29c24-176">Ensuite, créez une classe `public` nommée `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="29c24-176">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="29c24-177">Cette classe contient une liste d’objets `SurveyQuestion` et de méthodes permettant d’ajouter des questions à l’enquête, comme l’illustre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="29c24-177">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="29c24-178">Comme tout à l’heure, il faut initialiser l’objet de liste sur une valeur non Null pour éviter que le compilateur n’émette un avertissement.</span><span class="sxs-lookup"><span data-stu-id="29c24-178">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="29c24-179">Il n’y a pas de contrôle de type Null dans la deuxième surcharge de `AddQuestion`, car ce n’est pas nécessaire : vous avez déclaré cette variable comme étant non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-179">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="29c24-180">Sa valeur ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="29c24-180">Its value can't be `null`.</span></span>

<span data-ttu-id="29c24-181">Basculez vers `Program.cs` dans votre éditeur et remplacez le contenu de `Main` par les lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="29c24-181">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="29c24-182">Étant donné que l’ensemble du projet se trouve dans un contexte nullable, vous obtiendrez des avertissements lorsque vous transmettez `null` à n’importe quelle méthode qui attend un type de référence non nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-182">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="29c24-183">Regardez le résultat en ajoutant la ligne suivante à `Main` :</span><span class="sxs-lookup"><span data-stu-id="29c24-183">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="29c24-184">Créer des personnes interrogées et obtenir des réponses à l’enquête</span><span class="sxs-lookup"><span data-stu-id="29c24-184">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="29c24-185">Ensuite, écrivez le code qui génère des réponses à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-185">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="29c24-186">Ce processus implique plusieurs petites tâches :</span><span class="sxs-lookup"><span data-stu-id="29c24-186">This process involves several small tasks:</span></span>

1. <span data-ttu-id="29c24-187">Créer une méthode qui génère des objets personne interrogée,</span><span class="sxs-lookup"><span data-stu-id="29c24-187">Build a method that generates respondent objects.</span></span> <span data-ttu-id="29c24-188">représentant les personnes à qui il a été demandé de répondre à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-188">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="29c24-189">Créer une logique pour simuler les questions posées à une personne interrogée et les réponses obtenues, ou noter qu’une personne interrogée n’a pas répondu.</span><span class="sxs-lookup"><span data-stu-id="29c24-189">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="29c24-190">Répéter le processus jusqu'à ce que les personnes interrogées soient en nombre suffisant.</span><span class="sxs-lookup"><span data-stu-id="29c24-190">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="29c24-191">Il vous faut une classe qui représente les réponse à l’enquête. Ajoutez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="29c24-191">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="29c24-192">Activez la prise en charge Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-192">Enable nullable support.</span></span> <span data-ttu-id="29c24-193">Ajoutez une propriété `Id` et un constructeur qui l’initialise, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="29c24-193">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="29c24-194">Ensuite, ajoutez une méthode `static` pour créer de nouveaux participants en générant un ID aléatoire :</span><span class="sxs-lookup"><span data-stu-id="29c24-194">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="29c24-195">La responsabilité principale de cette classe consiste à générer les réponses d’un participant aux questions de l’enquête,</span><span class="sxs-lookup"><span data-stu-id="29c24-195">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="29c24-196">ce qui se décompose en plusieurs étapes :</span><span class="sxs-lookup"><span data-stu-id="29c24-196">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="29c24-197">Demander à participer à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="29c24-197">Ask for participation in the survey.</span></span> <span data-ttu-id="29c24-198">Si la personne refuse, renvoyer une réponse manquante (Null).</span><span class="sxs-lookup"><span data-stu-id="29c24-198">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="29c24-199">Poser chaque question et enregistrer la réponse.</span><span class="sxs-lookup"><span data-stu-id="29c24-199">Ask each question and record the answer.</span></span> <span data-ttu-id="29c24-200">Chacune des réponses peut également être manquante (Null).</span><span class="sxs-lookup"><span data-stu-id="29c24-200">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="29c24-201">Ajoutez le code suivant à la classe `SurveyResponse` :</span><span class="sxs-lookup"><span data-stu-id="29c24-201">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="29c24-202">Les réponses à l’enquête sont stockées dans un `Dictionary<int, string>?`, qui peut donc être Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-202">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="29c24-203">Vous utilisez la nouvelle fonctionnalité du langage pour déclarer votre intention de conception, à la fois au compilateur et à toute personne qui lira votre code.</span><span class="sxs-lookup"><span data-stu-id="29c24-203">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="29c24-204">Si vous déréférencez `surveyResponses` sans contrôler tout d’abord la valeur Null, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="29c24-204">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="29c24-205">La méthode `AnswerSurvey` ne génère pas d’avertissement, car le compilateur peut déterminer que la variable `surveyResponses` a été définie avant sur une valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="29c24-205">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="29c24-206">L’utilisation de `null` pour les réponses manquantes met en évidence un point important pour travailler avec les types référence nullable : votre objectif n’est pas de supprimer toutes les valeurs `null` à partir de votre programme.</span><span class="sxs-lookup"><span data-stu-id="29c24-206">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="29c24-207">Au lieu de cela, votre objectif est de vous assurer que le code que vous écrivez exprime l’intention de votre conception.</span><span class="sxs-lookup"><span data-stu-id="29c24-207">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="29c24-208">Les valeurs manquantes sont un concept nécessaire à exprimer dans votre code.</span><span class="sxs-lookup"><span data-stu-id="29c24-208">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="29c24-209">La valeur `null` est une méthode évidente pour exprimer les valeurs manquantes.</span><span class="sxs-lookup"><span data-stu-id="29c24-209">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="29c24-210">Essayer de supprimer toutes les valeurs `null` mène uniquement à la définition d’une autre façon d’exprimer ces valeurs manquantes sans `null`.</span><span class="sxs-lookup"><span data-stu-id="29c24-210">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="29c24-211">Ensuite, il reste à écrire la méthode `PerformSurvey` dans la classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="29c24-211">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="29c24-212">Ajoutez le code suivant à la classe `SurveyRun` :</span><span class="sxs-lookup"><span data-stu-id="29c24-212">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="29c24-213">Là encore, le choix d’une `List<SurveyResponse>?` Nullable indique que la réponse peut être Null,</span><span class="sxs-lookup"><span data-stu-id="29c24-213">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="29c24-214">et que l’enquête n’a pour le moment été menée auprès de personne.</span><span class="sxs-lookup"><span data-stu-id="29c24-214">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="29c24-215">Des personnes interrogées sont ajoutées jusqu'à ce qu’elles soient suffisamment nombreuses à avoir accepté.</span><span class="sxs-lookup"><span data-stu-id="29c24-215">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="29c24-216">La dernière étape consiste à ajouter un appel pour effectuer l’enquête à la fin de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="29c24-216">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="29c24-217">Examiner les réponses à l’enquête</span><span class="sxs-lookup"><span data-stu-id="29c24-217">Examine survey responses</span></span>

<span data-ttu-id="29c24-218">La dernière étape consiste à afficher les résultats de l’enquête,</span><span class="sxs-lookup"><span data-stu-id="29c24-218">The last step is to display survey results.</span></span> <span data-ttu-id="29c24-219">ce qui suppose d’ajouter du code à la plupart des classes déjà écrites.</span><span class="sxs-lookup"><span data-stu-id="29c24-219">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="29c24-220">Ce code montre l’intérêt de distinguer les types référence Nullable et non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-220">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="29c24-221">Commencez par ajouter les deux membres expression-bodied suivants à la classe `SurveyResponse` :</span><span class="sxs-lookup"><span data-stu-id="29c24-221">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="29c24-222">`surveyResponses` étant un type référence non Nullable, aucun contrôle n’est nécessaire avant de le déréférencer.</span><span class="sxs-lookup"><span data-stu-id="29c24-222">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="29c24-223">La méthode `Answer` retourne une chaîne non Nullable : choisissez la surcharge de `GetValueOrDefault` qui accepte un deuxième argument pour la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="29c24-223">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="29c24-224">Ensuite, ajoutez ces trois membres expression-bodied à la classe `SurveyRun` :</span><span class="sxs-lookup"><span data-stu-id="29c24-224">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="29c24-225">Le membre `AllParticipants` doit prendre en compte le fait que la variable `respondents` peut être Null, mais pas la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="29c24-225">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="29c24-226">Si vous modifiez cette expression en supprimant `??` et la séquence vide qui suit, le compilateur émet un avertissement, indiquant que la méthode peut retourner `null` et sa signature de retour un type non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-226">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="29c24-227">Enfin, ajoutez la boucle suivante en bas de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="29c24-227">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="29c24-228">Aucun contrôle `null` n’est nécessaire dans ce code, car vous avez conçu les interfaces sous-jacentes de sorte qu’elles retournent toutes des types référence non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-228">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="29c24-229">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="29c24-229">Get the code</span></span>

<span data-ttu-id="29c24-230">Pour obtenir le code du tutoriel complet, consultez notre dépôt [samples](https://github.com/dotnet/samples) dans le dossier [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="29c24-230">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="29c24-231">Faites des essais en modifiant les déclarations de type entre les types référence Nullable et non Nullable.</span><span class="sxs-lookup"><span data-stu-id="29c24-231">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="29c24-232">Examinez les différents avertissements générés, qui visent à empêcher de déréférencer accidentellement un `null`.</span><span class="sxs-lookup"><span data-stu-id="29c24-232">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="29c24-233">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="29c24-233">Next steps</span></span>

<span data-ttu-id="29c24-234">En savoir plus en migrant une application existante pour utiliser des types de référence nullable :</span><span class="sxs-lookup"><span data-stu-id="29c24-234">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="29c24-235">Mettre à niveau une application pour utiliser des types de référence nullable</span><span class="sxs-lookup"><span data-stu-id="29c24-235">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
