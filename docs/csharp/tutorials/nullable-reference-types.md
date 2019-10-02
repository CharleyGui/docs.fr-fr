---
title: Concevoir avec des types référence Nullable
description: Ce tutoriel avancé présente les types référence Nullable. Il explique comment exprimer une intention de conception lorsque les valeurs de référence peuvent être Null et comment, dans le cas contraire, indiquer au compilateur qu’elles ne peuvent pas être Null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 8b7c512a2f6bd67b07d8e344ad126026048be172
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736748"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Tutoriel : Exprimer plus clairement une intention de conception avec les types référence Nullable et non Nullable

C# 8 introduit les **types référence Nullable**, qui viennent compléter les types référence de la même façon que les types valeur Nullable complètent les types valeur. Pour déclarer une variable comme étant un **type référence Nullable**, on ajoute `?` au type. Par exemple, `string?` représente une `string` Nullable. Vous pouvez utiliser ces nouveaux types pour exprimer plus clairement votre intention de conception : certaines variables *doivent toujours avoir une valeur*, d’autres *peuvent ne pas en avoir*.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - incorporer des types référence Nullable et non Nullable dans vos conceptions ;
> - activer les contrôles de type référence Nullable dans l’ensemble de votre code ;
> - écrire du code permettant au compilateur d’appliquer ces décisions de conception ;
> - utiliser la fonctionnalité de référence Nullable dans vos propres conceptions.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le C# compilateur 8,0. Le C# compilateur 8 bêta est disponible avec [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou [.net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Incorporer des types référence Nullable dans des conceptions

Dans ce tutoriel, vous allez générer une bibliothèque qui modélise la réalisation d’une enquête. Le code utilise des types référence Nullable et non Nullable pour représenter les concepts du monde réel. Les questions de l’enquête ne peuvent jamais être Null. Si la personne interrogée ne souhaite pas répondre à une question, la réponse est Null.

Le code que vous allez écrire pour cet exemple exprime cette intention, que le compilateur se charge d’appliquer.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Créer l’application et activer les types référence Nullable

Créez une application console dans Visual Studio ou en ligne de commande avec `dotnet new console`. Nommez l'application `NullableIntroduction`. Une fois l’application créée, activez les fonctionnalités de la version C# 8 bêta. Ouvrez le fichier `csproj` et ajoutez un élément `LangVersion` à l'élément `PropertyGroup`. Vous devez cocher la fonctionnalité **Types référence Nullable**, même dans les projets C# 8. En effet, une fois la fonctionnalité activée, les déclarations de variables référence existantes deviennent des **types référence non Nullable**. Bien que cette décision aide à identifier les problèmes de contrôle de type Null dans le code, elle ne reflète pas forcément l’intention de conception d’origine. Activez la fonctionnalité en définissant l’élément `Nullable` sur `enable` :

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Concevoir les types de l’application

Cette application d’enquête implique la création d’un certain nombre de classes :

- une classe qui modélise la liste des questions ;
- une classe qui modélise la liste des personnes contactées pour l’enquête ;
- une classe qui modélise les réponses d’une personne ayant répondu à l’enquête.

Ces types utilisent des types référence Nullable et non Nullable pour indiquer quels membres sont requis et lesquels sont facultatifs. Les types référence Nullable communiquent clairement cette intention de conception :

- Les questions qui font partie de l’enquête ne peuvent jamais être Null : poser une question vide n’aurait pas de sens.
- Les personnes interrogées ne peuvent jamais être Null. Vous souhaitez faire un suivi des personnes que vous avez contactées, même de celles qui ont refusé de participer.
- La réponse à une question peut être Null. Les personnes interrogées peuvent refuser de répondre à certaines questions ou à la totalité d’entre elles.

Si vous avez déjà programmé en C#, vous avez peut-être une telle habitude des types référence qui autorisent les valeurs Null que vous avez raté certaines occasions de déclarer des instances non Nullable :

- La collection de questions doit être non Nullable.
- La collection de personnes interrogées doit être non Nullable.

En écrivant le code, vous allez voir qu’utiliser par défaut un type référence non Nullable pour les références permet d’éviter des erreurs courantes susceptibles d’aboutir à des exceptions de référence Null. Ce tutoriel vous aide à prendre des décisions sur les variables qui peuvent ou non être Null. Avant, le langage ne fournissait pas de syntaxe permettant d’exprimer ces décisions ; maintenant, si.

L’application que vous allez créer effectuera les opérations suivantes :

1. Créer une enquête et y ajouter des questions.
1. Créer un ensemble pseudo-aléatoire de personnes interrogées pour l’enquête.
1. Contacter les personnes interrogées jusqu'à ce que la taille de l’enquête réalisée atteigne le nombre visé.
1. Écrire des statistiques importantes sur les réponses à l’enquête.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Créer l’enquête avec des types Nullable et non Nullable

La première partie du code crée l’enquête. Vous allez écrire des classes pour modéliser une question et une enquête. L’enquête comporte trois types de questions, en fonction du format de la réponse : réponses par oui ou non, réponses chiffrées et réponses textuelles. Créez une classe `public` `SurveyQuestion` :

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Le compilateur interprète chaque déclaration de variable de type référence comme **non Nullable** pour le code dans un contexte nullable. Un premier avertissement apparaît lorsque l’on ajoute des propriétés pour le texte et le type de la question avec le code suivant :

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

Comme `QuestionText` n’est pas initialisé, le compilateur émet l’avertissement selon lequel une propriété non Nullable n’a pas été initialisée. Or, la conception exige que le texte de la question soit non Null. Ajoutez un constructeur pour l’initialiser, ainsi que la valeur `QuestionType`. Une fois terminée, la définition de classe se présente ainsi :

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Le fait d’ajouter le constructeur supprime l’avertissement. L’argument du constructeur étant également un type référence non Nullable, le compilateur ne génère pas d’avertissements.

Ensuite, créez une classe `public` nommée `SurveyRun`. Cette classe contient une liste d’objets `SurveyQuestion` et de méthodes permettant d’ajouter des questions à l’enquête, comme l’illustre le code suivant :

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

Comme tout à l’heure, il faut initialiser l’objet de liste sur une valeur non Null pour éviter que le compilateur n’émette un avertissement. Il n’y a pas de contrôle de type Null dans la deuxième surcharge de `AddQuestion`, car ce n’est pas nécessaire : vous avez déclaré cette variable comme étant non Nullable. Sa valeur ne peut pas être `null`.

Basculez vers `Program.cs` dans votre éditeur et remplacez le contenu de `Main` par les lignes de code suivantes :

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Étant donné que l’ensemble du projet se trouve dans un contexte nullable, vous obtiendrez des avertissements lorsque vous transmettez `null` à n’importe quelle méthode qui attend un type de référence non nullable. Regardez le résultat en ajoutant la ligne suivante à `Main` :

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Créer des personnes interrogées et obtenir des réponses à l’enquête

Ensuite, écrivez le code qui génère des réponses à l’enquête. Ce processus implique plusieurs petites tâches :

1. Créer une méthode qui génère des objets personne interrogée, représentant les personnes à qui il a été demandé de répondre à l’enquête.
1. Créer une logique pour simuler les questions posées à une personne interrogée et les réponses obtenues, ou noter qu’une personne interrogée n’a pas répondu.
1. Répéter le processus jusqu'à ce que les personnes interrogées soient en nombre suffisant.

Il vous faut une classe qui représente les réponse à l’enquête. Ajoutez-la maintenant. Activez la prise en charge Nullable. Ajoutez une propriété `Id` et un constructeur qui l’initialise, comme dans le code suivant :

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

Ensuite, ajoutez une méthode `static` pour créer de nouveaux participants en générant un ID aléatoire :

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

La responsabilité principale de cette classe consiste à générer les réponses d’un participant aux questions de l’enquête, ce qui se décompose en plusieurs étapes :

1. Demander à participer à l’enquête. Si la personne refuse, renvoyer une réponse manquante (Null).
1. Poser chaque question et enregistrer la réponse. Chacune des réponses peut également être manquante (Null).

Ajoutez le code suivant à la classe `SurveyResponse` :

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Les réponses à l’enquête sont stockées dans un `Dictionary<int, string>?`, qui peut donc être Null. Vous utilisez la nouvelle fonctionnalité du langage pour déclarer votre intention de conception, à la fois au compilateur et à toute personne qui lira votre code. Si vous déréférencez `surveyResponses` sans contrôler tout d’abord la valeur Null, le compilateur émet un avertissement. La méthode `AnswerSurvey` ne génère pas d’avertissement, car le compilateur peut déterminer que la variable `surveyResponses` a été définie avant sur une valeur non Null.

L’utilisation de `null` pour les réponses manquantes met en évidence un point important pour travailler avec les types référence nullable : votre objectif n’est pas de supprimer toutes les valeurs `null` à partir de votre programme. Au lieu de cela, votre objectif est de vous assurer que le code que vous écrivez exprime l’intention de votre conception. Les valeurs manquantes sont un concept nécessaire à exprimer dans votre code. La valeur `null` est une méthode évidente pour exprimer les valeurs manquantes. Essayer de supprimer toutes les valeurs `null` mène uniquement à la définition d’une autre façon d’exprimer ces valeurs manquantes sans `null`.

Ensuite, il reste à écrire la méthode `PerformSurvey` dans la classe `SurveyRun`. Ajoutez le code suivant à la classe `SurveyRun` :

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Là encore, le choix d’une `List<SurveyResponse>?` Nullable indique que la réponse peut être Null, et que l’enquête n’a pour le moment été menée auprès de personne. Des personnes interrogées sont ajoutées jusqu'à ce qu’elles soient suffisamment nombreuses à avoir accepté.

La dernière étape consiste à ajouter un appel pour effectuer l’enquête à la fin de la méthode `Main` :

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Examiner les réponses à l’enquête

La dernière étape consiste à afficher les résultats de l’enquête, ce qui suppose d’ajouter du code à la plupart des classes déjà écrites. Ce code montre l’intérêt de distinguer les types référence Nullable et non Nullable. Commencez par ajouter les deux membres expression-bodied suivants à la classe `SurveyResponse` :

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

`surveyResponses` étant un type référence non Nullable, aucun contrôle n’est nécessaire avant de le déréférencer. La méthode `Answer` retourne une chaîne non Nullable : choisissez la surcharge de `GetValueOrDefault` qui accepte un deuxième argument pour la valeur par défaut.

Ensuite, ajoutez ces trois membres expression-bodied à la classe `SurveyRun` :

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Le membre `AllParticipants` doit prendre en compte le fait que la variable `respondents` peut être Null, mais pas la valeur de retour. Si vous modifiez cette expression en supprimant `??` et la séquence vide qui suit, le compilateur émet un avertissement, indiquant que la méthode peut retourner `null` et sa signature de retour un type non Nullable.

Enfin, ajoutez la boucle suivante en bas de la méthode `Main` :

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Aucun contrôle `null` n’est nécessaire dans ce code, car vous avez conçu les interfaces sous-jacentes de sorte qu’elles retournent toutes des types référence non Nullable.

## <a name="get-the-code"></a>Obtenir le code

Pour obtenir le code du tutoriel complet, consultez notre dépôt [samples](https://github.com/dotnet/samples) dans le dossier [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).

Faites des essais en modifiant les déclarations de type entre les types référence Nullable et non Nullable. Examinez les différents avertissements générés, qui visent à empêcher de déréférencer accidentellement un `null`.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus en migrant une application existante pour utiliser des types de référence nullable :
> [!div class="nextstepaction"]
> [Mettre à niveau une application pour utiliser des types de référence nullable](upgrade-to-nullable-references.md)
