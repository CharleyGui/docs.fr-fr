---
title: 'Tutoriel : Écrire votre premier analyseur et correctif de code'
description: Ce tutoriel fournit des instructions détaillées pour générer un analyseur et un correctif de code à l’aide du SDK .NET Compiler (API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 23ebf4befc75e08592890d85f2dda51251f59cd6
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396281"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Tutoriel : Écrire votre premier analyseur et correctif de code

Le SDK .NET Compiler Platform fournit les outils nécessaires pour créer des avertissements personnalisés qui ciblent C# ou le code Visual Basic. Votre **analyseur** contient le code qui reconnaît les violations de votre règle. Votre **correctif de code** contient le code qui résout la violation. Les règles que vous implémentez peuvent aller de la structure du code au style de codage et aux conventions d’affectation de noms, et bien plus encore. .NET Compiler Platform fournit le framework permettant d’exécuter l’analyse alors que les développeurs écrivent du code, et toutes les fonctionnalités de l’IU Visual Studio pour corriger le code : afficher des tildes dans l’éditeur, renseigner la liste d’erreurs Visual Studio, créer des suggestions « ampoule » et afficher un aperçu détaillé des corrections suggérées.

Dans ce tutoriel, vous allez explorer la création d’un **analyseur** et d’un **correctif de code** associé à l’aide des API Roslyn. Un analyseur consiste à effectuer une analyse du code source et signaler un problème à l’utilisateur. Un analyseur peut également fournir un correctif de code qui représente une modification du code source de l’utilisateur. Ce tutoriel crée un analyseur qui recherche des déclarations de variables locales qui pourraient être déclarées à l’aide du modificateur `const` mais qui ne le sont pas. Le correctif de code associé modifie ces déclarations pour ajouter le modificateur `const`.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

Vous devez installer le kit de **développement logiciel (SDK) .NET Compiler Platform** via le Visual Studio installer :

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Il existe plusieurs étapes pour créer et valider votre analyseur :

1. Créez la solution.
1. Enregistrez le nom de l’analyseur et sa description.
1. Créez un rapport sur les avertissements et les recommandations de l’analyseur.
1. Implémentez le correctif de code pour accepter les recommandations.
1. Améliorez l’analyse par le biais de tests unitaires.

## <a name="explore-the-analyzer-template"></a>Explorer le modèle d’analyseur

Votre analyseur signale à l’utilisateur les déclarations de variables locales qui peuvent être converties en constantes locales. Considérons par exemple le code suivant :

```csharp
int x = 0;
Console.WriteLine(x);
```

Dans le code ci-dessus, une valeur constante est attribuée à `x` et n’est jamais modifiée. Elle peut être déclarée à l’aide du modificateur `const` :

```csharp
const int x = 0;
Console.WriteLine(x);
```

L’analyse pour déterminer si une variable peut être déclarée constante est impliquée, nécessitant une analyse syntaxique, une analyse constante de l’expression de l’initialiseur et une analyse du flux de données pour s’assurer que la variable n’est jamais accessible en écriture. .NET Compiler Platform fournit les API qui simplifient l’exécution de cette analyse. La première étape consiste à créer un nouveau projet C# **Analyseur avec correctif de code**.

- Dans Visual Studio, choisissez **Fichier > Nouveau > Projet...** pour afficher la boîte de dialogue Nouveau projet.
- Sous **Visual C# > Extensibilité**, choisissez **Analyseur avec correctif de code (.NET Standard)**.
- Nommez votre projet « **MakeConst** », puis cliquez sur OK.

Le modèle Analyseur avec correctif de code crée trois projets : un contient l’analyseur et le correctif de code, le second est un projet de test unitaire et le troisième est le projet VSIX. Le projet de démarrage par défaut est le projet VSIX. Appuyez sur **F5** pour démarrer le projet VSIX. Ceci démarre une deuxième instance de Visual Studio qui a chargé votre nouvel analyseur.

> [!TIP]
> Lorsque vous exécutez votre analyseur, vous démarrez une deuxième copie de Visual Studio. Cette deuxième copie utilise un hive de Registre différent pour stocker les paramètres. Cela vous permet de différencier les paramètres Visual dans les deux copies de Visual Studio. Vous pouvez choisir un autre thème pour l’exécution expérimentale de Visual Studio. En outre, ne rendez pas vos paramètres itinérants et ne vous connectez pas à votre compte Visual Studio à l’aide de l’exécution expérimentale de Visual Studio. Cela permet de conserver les paramètres différents.

Dans la deuxième instance de Visual Studio que vous venez de démarrer, créez un projet d’application console C# (.NET Core ou .NET Framework projet fonctionne, les analyseurs fonctionnent au niveau de la source.) Placez le curseur sur le jeton avec un soulignement ondulé et le texte d’avertissement fourni par un analyseur s’affiche.

Le modèle crée un analyseur qui émet un avertissement sur chaque déclaration de type dont le nom de type contient des lettres minuscules, comme indiqué dans la figure suivante :

![Avertissement de l’analyseur](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Le modèle fournit également un correctif de code qui modifie n’importe quel nom de type contenant des caractères minuscules en majuscules. Vous pouvez cliquer sur l’ampoule affichée avec l’avertissement pour voir les modifications suggérées. Le fait d’accepter les modifications suggérées met à jour le nom de type et toutes les références à ce type dans la solution. Maintenant que vous avez vu l’analyseur initial en action, fermez la deuxième instance de Visual Studio et revenez à votre projet d’analyseur.

Vous n’êtes pas obligé de démarrer une deuxième copie de Visual Studio et de créer un nouveau code pour tester chaque modification de votre analyseur. Le modèle crée également un projet de test unitaire pour vous. Ce projet contient deux tests. `TestMethod1` montre le format classique d’un test qui analyse le code sans déclencher un diagnostic. `TestMethod2` montre le format d’un test qui déclenche un diagnostic, puis applique un correctif de code proposé. À mesure que vous générez votre analyseur et votre correctif de code, vous écrirez des tests pour des structures de codes différentes afin de vérifier votre travail. Les tests unitaires pour les analyseurs sont beaucoup plus rapides que de les tester de manière interactive avec Visual Studio.

> [!TIP]
> Les tests unitaires d’analyseur sont un excellent outil lorsque vous savez quelles constructions de code doivent et ne doivent pas déclencher votre analyseur. Le chargement de votre analyseur dans une autre copie de Visual Studio est un excellent outil pour explorer et rechercher des constructions auxquelles vous n’avez peut-être pas encore pensé.

## <a name="create-analyzer-registrations"></a>Créer des enregistrements d’analyseur

Le modèle crée la classe `DiagnosticAnalyzer` initiale, dans le fichier **MakeConstAnalyzer.cs**. Cet analyseur initial montre deux propriétés importantes de chaque analyseur.

- Chaque analyseur de diagnostic doit fournir un attribut `[DiagnosticAnalyzer]` qui décrit le langage sur lequel il opère.
- Chaque analyseur de diagnostic doit dériver de la classe <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer>.

Le modèle montre également les fonctionnalités de base qui font partie de n’importe quel analyseur :

1. Enregistrer les actions. Les actions représentent les modifications de code qui doivent déclencher votre analyseur pour qu’il examine les violations dans le code. Lorsque Visual Studio détecte des modifications de code qui correspondent à une action enregistré, il appelle la méthode enregistrée de votre analyseur.
1. Créer des diagnostics. Quand votre analyseur détecte une violation, il crée un objet de diagnostic que Visual Studio utilise pour informer l’utilisateur de la violation.

Vous enregistrez des actions dans votre substitution de la méthode <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType>. Dans ce tutoriel, vous allez consulter des **nœuds de syntaxe** pour rechercher des déclarations locales et voir lesquelles ont des valeurs constantes. Si une déclaration peut être une constante, votre analyseur crée et signale un diagnostic.

La première étape consiste à mettre à jour les constantes d’inscription et la méthode `Initialize` pour que ces constantes indiquent votre analyseur « Make Const ». La plupart des constantes de chaîne est définie dans le fichier de ressources de chaîne. Cette pratique facilite la localisation. Ouvrez le fichier **Resources.resx** pour le projet d’analyseur **MakeConst**. Cela affiche l’éditeur de ressources. Mettez à jour les ressources de chaîne comme suit :

- Remplacez `AnalyzerTitle` par « Variable can be made constant » (La variable peut être rendue constante).
- Remplacez `AnalyzerMessageFormat` par « Can be made constant » (Peut être rendu constant).
- Remplacez `AnalyzerDescription` par « Make constant » (Rendre constant).

Modifiez aussi le menu déroulant **Modificateur d’accès** sur `public`. Ainsi, ces constantes sont plus faciles à utiliser dans les tests unitaires. Lorsque vous avez terminé, l’éditeur de ressources doit apparaître comme le montre l’illustration suivante :

![Mettre à jour les ressources de chaîne](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Les modifications restantes ont lieu dans le fichier de l’analyseur. Ouvrez **MakeConstAnalyzer.cs** dans Visual Studio. Modifiez l’action enregistrée d’une action qui agit sur les symboles à une action qui agit sur la syntaxe. Dans la méthode `MakeConstAnalyzerAnalyzer.Initialize`, recherchez la ligne qui enregistre l’action sur les symboles :

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Remplacez-la par la ligne suivante :

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Après cette modification, vous pouvez supprimer la méthode `AnalyzeSymbol`. Cet outil examine <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, et non les instructions <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>. Notez que `AnalyzeNode` est souligné par des traits ondulés rouges. Le code que vous venez d’ajouter référence une méthode `AnalyzeNode` qui n’a pas été déclarée. Déclarez cette méthode en utilisant le code suivant :

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Remplacez `Category` par « Usage » (Utilisation) dans **MakeConstAnalyzer.cs** comme illustré dans le code suivant :

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Rechercher des déclarations locales qui pourraient être constantes

Il est temps d’écrire la première version de la méthode `AnalyzeNode`. Elle doit rechercher une déclaration locale unique qui peut être `const` mais ne l’est pas, comme le code suivant :

```csharp
int x = 0;
Console.WriteLine(x);
```

La première étape consiste à rechercher les déclarations locales. Ajoutez le code suivant à `AnalyzeNode` dans **MakeConstAnalyzer.cs** :

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Ce cast réussit toujours, car votre analyseur a enregistré les modifications apportées aux déclarations locales, et uniquement les déclarations locales. Aucun autre type de nœud ne déclenche un appel à votre méthode `AnalyzeNode`. Ensuite, vérifiez la présence de modificateurs `const` dans la déclaration. Si vous en trouvez, retournez immédiatement. Le code suivant recherche les modificateurs `const` sur la déclaration locale :

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Enfin, vous devez vérifier que la variable peut être `const`. Cela signifie de s’assurer qu’elle n’est jamais assignée après son initialisation.

Vous allez effectuer une analyse sémantique à l’aide de <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>. Vous utilisez l’argument `context` pour déterminer si la déclaration de variable locale peut être rendue `const`. Un <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> représente toutes les informations sémantiques dans un fichier source unique. Vous pouvez en apprendre plus dans l’article qui traite des [modèles sémantiques](../work-with-semantics.md). Vous allez utiliser <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> pour effectuer une analyse de flux de données sur l’instruction de déclaration locale. Ensuite, vous utilisez les résultats de cette analyse de flux de données pour vous assurer que la variable locale n’est pas écrite avec une nouvelle valeur ailleurs. Appelez la méthode d’extension <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> pour récupérer <xref:Microsoft.CodeAnalysis.ILocalSymbol> pour la variable et vérifiez qu’il n’est pas contenu avec la collection <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> de l’analyse de flux de données. Ajoutez le code suivant à la fin de la méthode `AnalyzeNode` :

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Le code qui vient d’être ajouté garantit que la variable n’est pas modifiée et peut par conséquent devenir `const`. Il est temps de générer le diagnostic. Ajoutez le code suivant comme dernière ligne dans `AnalyzeNode` :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Vous pouvez vérifier votre progression en appuyant sur **F5** pour exécuter votre analyseur. Vous pouvez charger l’application console que vous avez créée précédemment et ajouter le code de test suivant :

```csharp
int x = 0;
Console.WriteLine(x);
```

L’ampoule doit apparaître et votre analyseur doit signaler un diagnostic. Toutefois, l’ampoule utilise toujours le correctif de code généré par le modèle et vous indique qu’il peut être converti en majuscules. La section suivante explique comment écrire le correctif de code.

## <a name="write-the-code-fix"></a>Écrire le correctif de code

Un analyseur peut fournir un ou plusieurs correctifs de code. Un correctif de code définit une modification qui traite le problème signalé. Pour l’analyseur que vous avez créé, vous pouvez fournir un correctif de code qui insère le mot clé const :

```csharp
const int x = 0;
Console.WriteLine(x);
```

L’utilisateur le choisit à partir de l’IU ampoule dans l’éditeur et Visual Studio modifie le code.

Ouvrez le fichier **MakeConstCodeFixProvider.cs** ajouté par le modèle.  Ce correctif de code est déjà associé à l’ID de diagnostic produit par votre analyseur de diagnostic, mais il n’implémente pas encore la transformation de code adéquate. Tout d’abord, vous devez supprimer une partie du code du modèle. Remplacez la chaîne de titre par « Make constant » :

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Ensuite, supprimez la méthode `MakeUppercaseAsync`. Elle n’est plus applicable.

Tous les fournisseurs de correctif de code dérivent de <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Ils substituent tous <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> pour signaler les correctifs de code disponibles. Dans `RegisterCodeFixesAsync`, remplacez le type de nœud ancêtre que vous recherchez par <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> pour faire correspondre le diagnostic :

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Ensuite, modifiez la dernière ligne pour enregistrer un correctif de code. Votre correctif crée un nouveau document obtenu en ajoutant le modificateur `const` à une déclaration existante :

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Notez les traits de soulignement ondulés rouges dans le code que vous venez d’ajouter sur le symbole `MakeConstAsync`. Ajoutez une déclaration pour `MakeConstAsync` comme le code suivant :

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Votre nouvelle méthode `MakeConstAsync` transformera <xref:Microsoft.CodeAnalysis.Document> qui représente le fichier source de l’utilisateur en un nouveau <xref:Microsoft.CodeAnalysis.Document> qui contient à présent une déclaration `const`.

Vous créez un nouveau jeton de mot clé `const` à insérer au début de l’instruction de déclaration. Veillez tout d’abord à supprimer les trivia de début dans le premier jeton de l’instruction de déclaration et à les associer au jeton `const`. Ajoutez le code suivant à la méthode `MakeConstAsync` :

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Ensuite, ajoutez le jeton `const` dans la déclaration à l’aide du code suivant :

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Ensuite, mettez en forme la nouvelle déclaration en fonction des règles de mise en forme en C#. La mise en forme de vos modifications pour correspondre au code existant crée une meilleure expérience. Ajoutez l’instruction suivante immédiatement après le code existant :

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Un nouvel espace de noms est requis pour ce code. Ajoutez la directive `using` suivante en haut du fichier :

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

L’étape finale consiste à apporter votre modification. Ce processus comprend trois étapes :

1. Obtenir un handle pour le document existant.
1. Créer un document en remplaçant la déclaration existante par la nouvelle déclaration.
1. Retourner le nouveau document.

Ajoutez le code suivant à la fin de la méthode `MakeConstAsync` :

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Votre correctif de code est prêt à être testé.  Appuyez sur F5 pour exécuter le projet d’analyseur dans une deuxième instance de Visual Studio. Dans la deuxième instance de Visual Studio, créez un projet Application console C# et ajoutez quelques déclarations de variables locales initialisées avec des valeurs constantes à la méthode Main. Vous verrez que ces éléments sont signalés en tant qu’avertissements comme indiqué ci-dessous.

![Avertissements Can make const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Vous avez bien progressé. Des traits de soulignement ondulés s’affichent sous les déclarations qui peuvent devenir `const`. Mais il reste encore du travail. Cela fonctionne si vous ajoutez `const` aux déclarations qui commencent par `i`, puis `j` et enfin `k`. Mais, si le modificateur `const` est ajouté dans un autre ordre, en commençant par `k`, l’analyseur crée des erreurs : `k` ne peut pas être déclaré `const`, sauf si `i` et `j` sont tous deux déjà `const`. Vous devez effectuer d’autres analyses afin de vous assurer que vous gérez les différentes façons dont les variables peuvent être déclarées et initialisées.

## <a name="build-data-driven-tests"></a>Générer des tests pilotés par les données

Votre analyseur et votre correctif de code travaillent sur un cas simple d’une déclaration unique qui peut être devenir constante. Il existe de nombreuses instructions de déclaration possibles où cette implémentation commet des erreurs. Vous allez traiter ces cas en travaillant avec la bibliothèque de tests unitaires écrite par le modèle. C’est beaucoup plus rapide que d’ouvrir plusieurs fois une deuxième copie de Visual Studio.

Ouvrez le fichier **MakeConstUnitTests.cs** dans le projet de test unitaire. Le modèle a créé deux tests qui suivent les deux modèles courants pour un test unitaire d’analyseur et de correctif de code. `TestMethod1` montre le modèle pour un test qui garantit que l’analyseur ne signale pas un diagnostic lorsqu’il ne le devrait pas. `TestMethod2` montre le modèle pour créer un rapport de diagnostic et exécuter le correctif de code.

Le code de presque chaque test pour votre analyseur suit un de ces deux modèles. Pour la première étape, vous pouvez revoir ces tests en tant que tests pilotés par les données. Ensuite, il sera facile de créer de nouveaux tests en ajoutant de nouvelles constantes de chaîne pour représenter les différentes entrées de test.

Pour plus d’efficacité, la première étape consiste à refactoriser les deux tests en tests pilotés par des données. Ensuite, il vous suffit de définir quelques constantes de chaîne pour chaque nouveau test. Pendant la refactorisation, renommez les deux méthodes avec des noms plus performants. Remplacez `TestMethod1` par ce test qui garantit qu’aucun diagnostic n’est déclenché :

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Vous pouvez créer une nouvelle ligne de données pour ce test en définissant un fragment de code qui ne doit pas entraîner votre diagnostic à déclencher un avertissement. Cette surcharge de passes `VerifyCSharpDiagnostic` lorsqu’il n’y a aucun diagnostic déclenché pour le fragment de code source.

Ensuite, remplacez `TestMethod2` par ce test qui garantit qu’un diagnostic est déclenché et un correctif de code appliqué pour le fragment de code source :

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

Le code précédent a apporté également quelques modifications au code qui génère le résultat de diagnostic attendu. Il utilise les constantes publiques enregistrées dans l’analyseur `MakeConst`. En outre, il utilise deux constantes de chaîne pour la source d’entrée et corrigée. Ajoutez les constantes de chaîne suivantes à la classe `UnitTest` :

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Exécutez ces deux tests pour vous assurer qu’ils réussissent. Dans Visual Studio, ouvrez **l’Explorateur de tests** en sélectionnant **Test** > **Windows** > **Explorateur de tests**.  Appuyez sur le lien **Exécuter tout**.

## <a name="create-tests-for-valid-declarations"></a>Créer des tests pour les déclarations valides

En règle générale, les analyseurs doivent s’arrêter aussi rapidement que possible, en effectuant un minimum de travail. Visual Studio appelle les analyseurs enregistrés lorsque l’utilisateur modifie le code. La réactivité est essentielle. Il existe plusieurs cas de test pour le code qui ne doivent pas déclencher votre diagnostic. Votre analyseur a déjà géré l’un de ces tests, le cas où une variable est assignée après avoir été initialisée. Ajoutez la constante de chaîne suivante à vos tests pour représenter ce cas :

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Ensuite, ajoutez une ligne de données pour ce test, comme indiqué dans l’extrait de code ci-dessous :

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Ce test réussit également. Ensuite, ajoutez des constantes pour les conditions que vous n’avez pas encore gérées :

- Déclarations qui sont déjà `const`, car elles sont déjà constantes :

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Déclarations sans initialiseur, car il n’existe aucune valeur à utiliser :

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Déclarations où l’initialiseur n’est pas une constante, car elles ne peuvent pas être des constantes de compilation :

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Cela peut être encore plus compliqué, car C# accepte que plusieurs déclarations forment une seule instruction. Prenez en compte la constante de chaîne de cas de test suivante :

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

La variable `i` peut devenir constante, mais la variable `j` ne le peut pas. Par conséquent, cette instruction ne peut pas devenir une déclaration constante. Ajouter les déclarations `DataRow` pour tous ces tests :

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Réexécutez vos tests, et vous verrez ces nouveaux cas de test échouent.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Mettre à jour votre analyseur afin d’ignorer les déclarations correctes

Vous avez besoin de certaines améliorations dans la méthode `AnalyzeNode` de votre analyseur pour éliminer le code correspondant à ces conditions. Ce sont toutes des conditions associées, donc des modifications similaires résoudront toutes ces conditions. Dans `AnalyzeNode`, effectuez les changements suivants :

- Votre analyse sémantique a examiné une déclaration de variable unique. Ce code doit se trouver dans une boucle `foreach` qui examine toutes les variables déclarées dans la même instruction.
- Chaque variable déclarée doit avoir un initialiseur.
- L’initialiseur de chaque variable déclarée doit être une constante de compilation.

Dans votre méthode `AnalyzeNode`, remplacez l’analyse sémantique d’origine :

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

par l’extrait de code suivant :

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

La première boucle `foreach` examine chaque déclaration de variable à l’aide de l’analyse syntaxique. La première vérification garantit que la variable a un initialiseur. La deuxième vérification garantit que l’initialiseur est une constante. La deuxième boucle contient l’analyse sémantique d’origine. Les vérifications sémantiques sont dans une boucle distincte, car elles ont un impact plus important sur les performances. Réexécutez vos tests. Ils doivent tous réussir.

## <a name="add-the-final-polish"></a>Ajouter la touche finale

Vous avez presque terminé. Il existe quelques conditions de plus que votre analyseur doit gérer. Visual Studio appelle les analyseurs lorsque l’utilisateur écrit du code. Souvent, votre analyseur sera appelé lorsque du code ne se compile pas. La méthode `AnalyzeNode` de votre analyseur de diagnostic ne vérifie pas si la valeur de constante est convertible en type de variable. Par conséquent, l’implémentation actuelle convertit sans problème une déclaration incorrecte comme int i = « abc » en une constante locale. Ajoutez une constante de chaîne source pour cette condition :

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

En outre, les types de référence ne sont pas gérés correctement. La seule valeur de constante autorisée pour un type de référence est `null`, sauf dans le cas de <xref:System.String?displayProperty=nameWithType>, qui autorise des littéraux de chaîne. En d’autres termes, `const string s = "abc"` est légal, mais pas `const object s = "abc"`. Cet extrait de code vérifie cette condition :

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Pour être exhaustif, vous devez ajouter un autre test afin de vous assurer que vous pouvez créer une déclaration de constante pour une chaîne. L’extrait de code suivant définit le code qui déclenche le diagnostic et le code une fois que le correctif a été appliqué :

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Enfin, si une variable est déclarée avec le mot clé `var`, le correctif de code fait la mauvaise chose et génère une déclaration `const var`, qui n’est pas prise en charge par le langage C#. Pour corriger ce bogue, le correctif de code doit remplacer le mot clé `var` par le nom du type déduit :

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Ces modifications mettent à jour les déclarations de ligne de données pour les deux tests. Le code suivant montre ces tests avec tous les attributs de ligne de données :

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Heureusement, tous les bogues ci-dessus peuvent être gérés à l’aide des mêmes techniques que celles que vous venez d’apprendre.

Pour corriger le premier bogue, commencez par ouvrir **DiagnosticAnalyzer.cs** et recherchez la boucle foreach où chacun des initialiseurs de la déclaration locale est vérifié pour s’assurer que des valeurs constantes leur sont attribués. Immédiatement _avant_ la première boucle foreach, appelez `context.SemanticModel.GetTypeInfo()` pour récupérer des informations détaillées sur le type déclaré de la déclaration locale :

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Ensuite, dans votre boucle `foreach`, vérifiez chaque initialiseur pour vous assurer qu’il peut être converti dans le type de variable. Ajoutez la vérification suivante après avoir vérifié que l’initialiseur est une constante :

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

La modification suivante s’appuie sur la précédente. Avant l’accolade fermante de la première boucle foreach, ajoutez le code suivant pour vérifier le type de la déclaration locale si la constante est une chaîne ou une valeur null.

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

Vous devez écrire un peu plus de code dans votre fournisseur de correctif de code pour remplacer le mot clé var' par le nom de type correct. Revenez dans **CodeFixProvider.cs**. Le code que vous ajouterez effectue les étapes suivantes :

- Vérifiez si la déclaration est une déclaration `var`, et dans ce cas :
- Créez un nouveau type pour le type déduit.
- Assurez-vous que la déclaration de type n’est pas un alias. Le cas échéant, il est permis de déclarer `const var`.
- Assurez-vous que `var` n’est pas un nom de type dans ce programme. (Dans ce cas, `const var` est autorisé).
- Simplifier le nom de type complet

On dirait que beaucoup de code est nécessaire pour cela. Ce n’est pas le cas. Remplacez la ligne qui déclare et initialise `newLocal` par le code suivant. Il se place immédiatement après l’initialisation de `newModifiers` :

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Vous devez ajouter une `using` directive pour utiliser le <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type :

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Exécutez vos tests. Ils doivent tous réussir. Félicitez-vous en exécutant votre analyseur terminé. Appuyez sur Ctrl+F5 pour exécuter le projet d’analyseur dans une deuxième instance de Visual Studio avec l’extension Préversion Roslyn chargée.

- Dans la deuxième instance de Visual Studio, créez un projet Application console C# et ajoutez `int x = "abc";` à la méthode Main. Grâce à la correction du premier bogue, aucun avertissement ne doit être signalé pour cette déclaration de variable locale (même s’il existe une erreur du compilateur comme prévu).
- Ensuite, ajoutez `object s = "abc";` à la méthode Main. En raison de la correction du deuxième bogue, aucun avertissement ne doit être signalé.
- Enfin, ajoutez une autre variable locale qui utilise le mot clé `var`. Un avertissement est signalé et une suggestion apparaît en dessous à gauche.
- Déplacez le signe d’insertion de l’éditeur sur le trait de soulignement ondulé et appuyez sur Ctrl+. pour afficher le correctif de code suggéré. Lors de la sélection de votre correctif de code, notez que le mot clé ' var' est désormais géré correctement.

Enfin, ajoutez le code suivant :

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Après ces modifications, vous obtenez des traits de soulignement ondulés rouges uniquement sur les deux premières variables. Ajoutez `const` à `i` et à `j`, et vous obtenez un nouvel avertissement sur `k`, car cet élément peut désormais devenir `const`.

Félicitations ! Vous avez créé votre première extension .NET Compiler Platform qui effectue une analyse de code à la volée pour détecter un problème et fournit une solution rapide pour résoudre ce problème. Tout au long du processus, vous avez découvert la plupart des API de code qui font partie du SDK .NET Compiler Platform (API Roslyn). Vous pouvez comparer votre travail avec [l’exemple terminé](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) dans notre référentiel GitHub d’exemples.

## <a name="other-resources"></a>Autres ressources

- [Bien démarrer avec l’analyse de la syntaxe](../get-started/syntax-analysis.md)
- [Bien démarrer avec l’analyse sémantique](../get-started/semantic-analysis.md)
