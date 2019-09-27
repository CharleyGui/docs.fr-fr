---
title: Concevoir avec des types référence Nullable
description: Ce tutoriel avancé présente les types référence Nullable. Il explique comment exprimer une intention de conception lorsque les valeurs de référence peuvent être Null et comment, dans le cas contraire, indiquer au compilateur qu’elles ne peuvent pas être Null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 6b127cce66f2f9ced3cee29336b39e2976e03619
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332342"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="d8595-104">Tutoriel : Exprimer plus clairement une intention de conception avec les types référence Nullable et non Nullable</span><span class="sxs-lookup"><span data-stu-id="d8595-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="d8595-105">C# 8 introduit les **types référence Nullable**, qui viennent compléter les types référence de la même façon que les types valeur Nullable complètent les types valeur.</span><span class="sxs-lookup"><span data-stu-id="d8595-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="d8595-106">Pour déclarer une variable comme étant un **type référence Nullable**, on ajoute `?` au type.</span><span class="sxs-lookup"><span data-stu-id="d8595-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="d8595-107">Par exemple, `string?` représente une `string` Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="d8595-108">Vous pouvez utiliser ces nouveaux types pour exprimer plus clairement votre intention de conception : certaines variables *doivent toujours avoir une valeur*, d’autres *peuvent ne pas en avoir*.</span><span class="sxs-lookup"><span data-stu-id="d8595-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="d8595-109">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="d8595-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d8595-110">incorporer des types référence Nullable et non Nullable dans vos conceptions ;</span><span class="sxs-lookup"><span data-stu-id="d8595-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="d8595-111">activer les contrôles de type référence Nullable dans l’ensemble de votre code ;</span><span class="sxs-lookup"><span data-stu-id="d8595-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="d8595-112">écrire du code permettant au compilateur d’appliquer ces décisions de conception ;</span><span class="sxs-lookup"><span data-stu-id="d8595-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="d8595-113">utiliser la fonctionnalité de référence Nullable dans vos propres conceptions.</span><span class="sxs-lookup"><span data-stu-id="d8595-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8595-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d8595-114">Prerequisites</span></span>

<span data-ttu-id="d8595-115">Vous devrez configurer votre ordinateur de façon à exécuter .NET Core, avec le compilateur C# 8.0 bêta.</span><span class="sxs-lookup"><span data-stu-id="d8595-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="d8595-116">Le C# compilateur 8 bêta est disponible avec [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou [.net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="d8595-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="d8595-117">Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8595-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="d8595-118">Incorporer des types référence Nullable dans des conceptions</span><span class="sxs-lookup"><span data-stu-id="d8595-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="d8595-119">Dans ce tutoriel, vous allez générer une bibliothèque qui modélise la réalisation d’une enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="d8595-120">Le code utilise des types référence Nullable et non Nullable pour représenter les concepts du monde réel.</span><span class="sxs-lookup"><span data-stu-id="d8595-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="d8595-121">Les questions de l’enquête ne peuvent jamais être Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-121">The survey questions can never be null.</span></span> <span data-ttu-id="d8595-122">Si la personne interrogée ne souhaite pas répondre à une question,</span><span class="sxs-lookup"><span data-stu-id="d8595-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="d8595-123">la réponse est Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-123">The responses might be null in this case.</span></span>

<span data-ttu-id="d8595-124">Le code que vous allez écrire pour cet exemple exprime cette intention, que le compilateur se charge d’appliquer.</span><span class="sxs-lookup"><span data-stu-id="d8595-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="d8595-125">Créer l’application et activer les types référence Nullable</span><span class="sxs-lookup"><span data-stu-id="d8595-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="d8595-126">Créez une application console dans Visual Studio ou en ligne de commande avec `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="d8595-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="d8595-127">Nommez l'application `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="d8595-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="d8595-128">Une fois l’application créée, activez les fonctionnalités de la version C# 8 bêta.</span><span class="sxs-lookup"><span data-stu-id="d8595-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="d8595-129">Ouvrez le fichier `csproj` et ajoutez un élément `LangVersion` à l'élément `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="d8595-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="d8595-130">Vous devez cocher la fonctionnalité **Types référence Nullable**, même dans les projets C# 8.</span><span class="sxs-lookup"><span data-stu-id="d8595-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="d8595-131">En effet, une fois la fonctionnalité activée, les déclarations de variables référence existantes deviennent des **types référence non Nullable**.</span><span class="sxs-lookup"><span data-stu-id="d8595-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="d8595-132">Bien que cette décision aide à identifier les problèmes de contrôle de type Null dans le code, elle ne reflète pas forcément l’intention de conception d’origine.</span><span class="sxs-lookup"><span data-stu-id="d8595-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="d8595-133">Activez la fonctionnalité en définissant l’élément `Nullable` sur `enable` :</span><span class="sxs-lookup"><span data-stu-id="d8595-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="d8595-134">Concevoir les types de l’application</span><span class="sxs-lookup"><span data-stu-id="d8595-134">Design the types for the application</span></span>

<span data-ttu-id="d8595-135">Cette application d’enquête implique la création d’un certain nombre de classes :</span><span class="sxs-lookup"><span data-stu-id="d8595-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="d8595-136">une classe qui modélise la liste des questions ;</span><span class="sxs-lookup"><span data-stu-id="d8595-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="d8595-137">une classe qui modélise la liste des personnes contactées pour l’enquête ;</span><span class="sxs-lookup"><span data-stu-id="d8595-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="d8595-138">une classe qui modélise les réponses d’une personne ayant répondu à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="d8595-139">Ces types utilisent des types référence Nullable et non Nullable pour indiquer quels membres sont requis et lesquels sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="d8595-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="d8595-140">Les types référence Nullable communiquent clairement cette intention de conception :</span><span class="sxs-lookup"><span data-stu-id="d8595-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="d8595-141">Les questions qui font partie de l’enquête ne peuvent jamais être Null : poser une question vide n’aurait pas de sens.</span><span class="sxs-lookup"><span data-stu-id="d8595-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="d8595-142">Les personnes interrogées ne peuvent jamais être Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-142">The respondents can never be null.</span></span> <span data-ttu-id="d8595-143">Vous souhaitez faire un suivi des personnes que vous avez contactées, même de celles qui ont refusé de participer.</span><span class="sxs-lookup"><span data-stu-id="d8595-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="d8595-144">La réponse à une question peut être Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-144">Any response to a question may be null.</span></span> <span data-ttu-id="d8595-145">Les personnes interrogées peuvent refuser de répondre à certaines questions ou à la totalité d’entre elles.</span><span class="sxs-lookup"><span data-stu-id="d8595-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="d8595-146">Si vous avez déjà programmé en C#, vous avez peut-être une telle habitude des types référence qui autorisent les valeurs Null que vous avez raté certaines occasions de déclarer des instances non Nullable :</span><span class="sxs-lookup"><span data-stu-id="d8595-146">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="d8595-147">La collection de questions doit être non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="d8595-148">La collection de personnes interrogées doit être non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="d8595-149">En écrivant le code, vous allez voir qu’utiliser par défaut un type référence non Nullable pour les références permet d’éviter des erreurs courantes susceptibles d’aboutir à des exceptions de référence Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="d8595-150">Ce tutoriel vous aide à prendre des décisions sur les variables qui peuvent ou non être Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-150">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="d8595-151">Avant, le langage ne fournissait pas de syntaxe permettant d’exprimer ces décisions ;</span><span class="sxs-lookup"><span data-stu-id="d8595-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="d8595-152">maintenant, si.</span><span class="sxs-lookup"><span data-stu-id="d8595-152">Now it does.</span></span>

<span data-ttu-id="d8595-153">L’application que vous allez créer effectuera les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8595-153">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="d8595-154">Créer une enquête et y ajouter des questions.</span><span class="sxs-lookup"><span data-stu-id="d8595-154">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="d8595-155">Créer un ensemble pseudo-aléatoire de personnes interrogées pour l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-155">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="d8595-156">Contacter les personnes interrogées jusqu'à ce que la taille de l’enquête réalisée atteigne le nombre visé.</span><span class="sxs-lookup"><span data-stu-id="d8595-156">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="d8595-157">Écrire des statistiques importantes sur les réponses à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-157">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="d8595-158">Créer l’enquête avec des types Nullable et non Nullable</span><span class="sxs-lookup"><span data-stu-id="d8595-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="d8595-159">La première partie du code crée l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="d8595-160">Vous allez écrire des classes pour modéliser une question et une enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="d8595-161">L’enquête comporte trois types de questions, en fonction du format de la réponse : réponses par oui ou non, réponses chiffrées et réponses textuelles.</span><span class="sxs-lookup"><span data-stu-id="d8595-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="d8595-162">Créez une classe `public` `SurveyQuestion` :</span><span class="sxs-lookup"><span data-stu-id="d8595-162">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="d8595-163">Le compilateur interprète chaque déclaration de variable de type référence comme **non Nullable** pour le code dans un contexte nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="d8595-164">Un premier avertissement apparaît lorsque l’on ajoute des propriétés pour le texte et le type de la question avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8595-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="d8595-165">Comme `QuestionText` n’est pas initialisé, le compilateur émet l’avertissement selon lequel une propriété non Nullable n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="d8595-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="d8595-166">Or, la conception exige que le texte de la question soit non Null. Ajoutez un constructeur pour l’initialiser, ainsi que la valeur `QuestionType`.</span><span class="sxs-lookup"><span data-stu-id="d8595-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="d8595-167">Une fois terminée, la définition de classe se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="d8595-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="d8595-168">Le fait d’ajouter le constructeur supprime l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="d8595-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="d8595-169">L’argument du constructeur étant également un type référence non Nullable, le compilateur ne génère pas d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="d8595-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="d8595-170">Ensuite, créez une classe `public` nommée `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="d8595-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="d8595-171">Cette classe contient une liste d’objets `SurveyQuestion` et de méthodes permettant d’ajouter des questions à l’enquête, comme l’illustre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8595-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="d8595-172">Comme tout à l’heure, il faut initialiser l’objet de liste sur une valeur non Null pour éviter que le compilateur n’émette un avertissement.</span><span class="sxs-lookup"><span data-stu-id="d8595-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="d8595-173">Il n’y a pas de contrôle de type Null dans la deuxième surcharge de `AddQuestion`, car ce n’est pas nécessaire : vous avez déclaré cette variable comme étant non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="d8595-174">Sa valeur ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="d8595-174">Its value can't be `null`.</span></span>

<span data-ttu-id="d8595-175">Basculez vers `Program.cs` dans votre éditeur et remplacez le contenu de `Main` par les lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8595-175">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="d8595-176">Étant donné que l’ensemble du projet se trouve dans un contexte nullable, vous obtiendrez des avertissements lorsque vous transmettez `null` à n’importe quelle méthode qui attend un type de référence non nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-176">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="d8595-177">Regardez le résultat en ajoutant la ligne suivante à `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8595-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="d8595-178">Créer des personnes interrogées et obtenir des réponses à l’enquête</span><span class="sxs-lookup"><span data-stu-id="d8595-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="d8595-179">Ensuite, écrivez le code qui génère des réponses à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="d8595-180">Ce processus implique plusieurs petites tâches :</span><span class="sxs-lookup"><span data-stu-id="d8595-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="d8595-181">Créer une méthode qui génère des objets personne interrogée,</span><span class="sxs-lookup"><span data-stu-id="d8595-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="d8595-182">représentant les personnes à qui il a été demandé de répondre à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="d8595-183">Créer une logique pour simuler les questions posées à une personne interrogée et les réponses obtenues, ou noter qu’une personne interrogée n’a pas répondu.</span><span class="sxs-lookup"><span data-stu-id="d8595-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="d8595-184">Répéter le processus jusqu'à ce que les personnes interrogées soient en nombre suffisant.</span><span class="sxs-lookup"><span data-stu-id="d8595-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="d8595-185">Il vous faut une classe qui représente les réponse à l’enquête. Ajoutez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="d8595-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="d8595-186">Activez la prise en charge Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-186">Enable nullable support.</span></span> <span data-ttu-id="d8595-187">Ajoutez une propriété `Id` et un constructeur qui l’initialise, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8595-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="d8595-188">Ensuite, ajoutez une méthode `static` pour créer de nouveaux participants en générant un ID aléatoire :</span><span class="sxs-lookup"><span data-stu-id="d8595-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="d8595-189">La responsabilité principale de cette classe consiste à générer les réponses d’un participant aux questions de l’enquête,</span><span class="sxs-lookup"><span data-stu-id="d8595-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="d8595-190">ce qui se décompose en plusieurs étapes :</span><span class="sxs-lookup"><span data-stu-id="d8595-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="d8595-191">Demander à participer à l’enquête.</span><span class="sxs-lookup"><span data-stu-id="d8595-191">Ask for participation in the survey.</span></span> <span data-ttu-id="d8595-192">Si la personne refuse, renvoyer une réponse manquante (Null).</span><span class="sxs-lookup"><span data-stu-id="d8595-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="d8595-193">Poser chaque question et enregistrer la réponse.</span><span class="sxs-lookup"><span data-stu-id="d8595-193">Ask each question and record the answer.</span></span> <span data-ttu-id="d8595-194">Chacune des réponses peut également être manquante (Null).</span><span class="sxs-lookup"><span data-stu-id="d8595-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="d8595-195">Ajoutez le code suivant à la classe `SurveyResponse` :</span><span class="sxs-lookup"><span data-stu-id="d8595-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="d8595-196">Les réponses à l’enquête sont stockées dans un `Dictionary<int, string>?`, qui peut donc être Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="d8595-197">Vous utilisez la nouvelle fonctionnalité du langage pour déclarer votre intention de conception, à la fois au compilateur et à toute personne qui lira votre code.</span><span class="sxs-lookup"><span data-stu-id="d8595-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="d8595-198">Si vous déréférencez `surveyResponses` sans contrôler tout d’abord la valeur Null, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="d8595-198">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="d8595-199">La méthode `AnswerSurvey` ne génère pas d’avertissement, car le compilateur peut déterminer que la variable `surveyResponses` a été définie avant sur une valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="d8595-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="d8595-200">L’utilisation de `null` pour les réponses manquantes met en évidence un point important pour travailler avec les types référence nullable : votre objectif n’est pas de supprimer toutes les valeurs `null` à partir de votre programme.</span><span class="sxs-lookup"><span data-stu-id="d8595-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="d8595-201">Au lieu de cela, votre objectif est de vous assurer que le code que vous écrivez exprime l’intention de votre conception.</span><span class="sxs-lookup"><span data-stu-id="d8595-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="d8595-202">Les valeurs manquantes sont un concept nécessaire à exprimer dans votre code.</span><span class="sxs-lookup"><span data-stu-id="d8595-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="d8595-203">La valeur `null` est une méthode évidente pour exprimer les valeurs manquantes.</span><span class="sxs-lookup"><span data-stu-id="d8595-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="d8595-204">Essayer de supprimer toutes les valeurs `null` mène uniquement à la définition d’une autre façon d’exprimer ces valeurs manquantes sans `null`.</span><span class="sxs-lookup"><span data-stu-id="d8595-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="d8595-205">Ensuite, il reste à écrire la méthode `PerformSurvey` dans la classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="d8595-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="d8595-206">Ajoutez le code suivant à la classe `SurveyRun` :</span><span class="sxs-lookup"><span data-stu-id="d8595-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="d8595-207">Là encore, le choix d’une `List<SurveyResponse>?` Nullable indique que la réponse peut être Null,</span><span class="sxs-lookup"><span data-stu-id="d8595-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="d8595-208">et que l’enquête n’a pour le moment été menée auprès de personne.</span><span class="sxs-lookup"><span data-stu-id="d8595-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="d8595-209">Des personnes interrogées sont ajoutées jusqu'à ce qu’elles soient suffisamment nombreuses à avoir accepté.</span><span class="sxs-lookup"><span data-stu-id="d8595-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="d8595-210">La dernière étape consiste à ajouter un appel pour effectuer l’enquête à la fin de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8595-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="d8595-211">Examiner les réponses à l’enquête</span><span class="sxs-lookup"><span data-stu-id="d8595-211">Examine survey responses</span></span>

<span data-ttu-id="d8595-212">La dernière étape consiste à afficher les résultats de l’enquête,</span><span class="sxs-lookup"><span data-stu-id="d8595-212">The last step is to display survey results.</span></span> <span data-ttu-id="d8595-213">ce qui suppose d’ajouter du code à la plupart des classes déjà écrites.</span><span class="sxs-lookup"><span data-stu-id="d8595-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="d8595-214">Ce code montre l’intérêt de distinguer les types référence Nullable et non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="d8595-215">Commencez par ajouter les deux membres expression-bodied suivants à la classe `SurveyResponse` :</span><span class="sxs-lookup"><span data-stu-id="d8595-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="d8595-216">`surveyResponses` étant un type référence non Nullable, aucun contrôle n’est nécessaire avant de le déréférencer.</span><span class="sxs-lookup"><span data-stu-id="d8595-216">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="d8595-217">La méthode `Answer` retourne une chaîne non Nullable : choisissez la surcharge de `GetValueOrDefault` qui accepte un deuxième argument pour la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d8595-217">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="d8595-218">Ensuite, ajoutez ces trois membres expression-bodied à la classe `SurveyRun` :</span><span class="sxs-lookup"><span data-stu-id="d8595-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="d8595-219">Le membre `AllParticipants` doit prendre en compte le fait que la variable `respondents` peut être Null, mais pas la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="d8595-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="d8595-220">Si vous modifiez cette expression en supprimant `??` et la séquence vide qui suit, le compilateur émet un avertissement, indiquant que la méthode peut retourner `null` et sa signature de retour un type non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="d8595-221">Enfin, ajoutez la boucle suivante en bas de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8595-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="d8595-222">Aucun contrôle `null` n’est nécessaire dans ce code, car vous avez conçu les interfaces sous-jacentes de sorte qu’elles retournent toutes des types référence non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="d8595-223">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="d8595-223">Get the code</span></span>

<span data-ttu-id="d8595-224">Pour obtenir le code du tutoriel complet, consultez notre dépôt [samples](https://github.com/dotnet/samples) dans le dossier [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="d8595-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="d8595-225">Faites des essais en modifiant les déclarations de type entre les types référence Nullable et non Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8595-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="d8595-226">Examinez les différents avertissements générés, qui visent à empêcher de déréférencer accidentellement un `null`.</span><span class="sxs-lookup"><span data-stu-id="d8595-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d8595-227">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d8595-227">Next steps</span></span>

<span data-ttu-id="d8595-228">En savoir plus en migrant une application existante pour utiliser des types de référence nullable :</span><span class="sxs-lookup"><span data-stu-id="d8595-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d8595-229">Mettre à niveau une application pour utiliser des types de référence nullable</span><span class="sxs-lookup"><span data-stu-id="d8595-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
