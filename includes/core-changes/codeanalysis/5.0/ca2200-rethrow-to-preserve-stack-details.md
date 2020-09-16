---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538920"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="662ba-101">CA2200 : Levez à nouveau une exception pour conserver les détails de la pile</span><span class="sxs-lookup"><span data-stu-id="662ba-101">CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="662ba-102">La règle d’analyseur de code .NET [ca2200](/visualstudio/code-quality/ca2200) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="662ba-102">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="662ba-103">Il génère un avertissement de génération pour tous les `catch` blocs qui lèvent à nouveau une exception et l’exception est explicitement spécifiée dans l' `throw` instruction.</span><span class="sxs-lookup"><span data-stu-id="662ba-103">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

#### <a name="change-description"></a><span data-ttu-id="662ba-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="662ba-104">Change description</span></span>

<span data-ttu-id="662ba-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="662ba-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="662ba-106">Plusieurs de ces règles sont activées par défaut, y compris [ca2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="662ba-106">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="662ba-107">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="662ba-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="662ba-108">Règle ca2200 signale le code où les exceptions sont levées à nouveau et la variable d’exception est spécifiée dans l' `throw` instruction.</span><span class="sxs-lookup"><span data-stu-id="662ba-108">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="662ba-109">Lorsqu’une exception est levée, une partie des informations qu’elle transmet est la trace de la pile.</span><span class="sxs-lookup"><span data-stu-id="662ba-109">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="662ba-110">La trace de la pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception.</span><span class="sxs-lookup"><span data-stu-id="662ba-110">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="662ba-111">Si une exception est levée à nouveau en spécifiant l’exception dans l' `throw` instruction, la trace de la pile redémarre à la méthode actuelle et la liste des appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue.</span><span class="sxs-lookup"><span data-stu-id="662ba-111">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="662ba-112">Pour conserver les informations de trace de la pile d’origine avec l’exception, utilisez l' `throw` instruction sans spécifier l’exception.</span><span class="sxs-lookup"><span data-stu-id="662ba-112">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="662ba-113">L’extrait de code suivant ne génère pas d’avertissement pour la règle ca2200.</span><span class="sxs-lookup"><span data-stu-id="662ba-113">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="662ba-114">Toutefois, la *ligne commentée déclencherait* une violation.</span><span class="sxs-lookup"><span data-stu-id="662ba-114">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a><span data-ttu-id="662ba-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="662ba-115">Version introduced</span></span>

<span data-ttu-id="662ba-116">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="662ba-116">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="662ba-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="662ba-117">Recommended action</span></span>

- <span data-ttu-id="662ba-118">Lever à nouveau les exceptions sans spécifier explicitement l’exception.</span><span class="sxs-lookup"><span data-stu-id="662ba-118">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="662ba-119">Pour plus d’informations, voir [ca2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="662ba-119">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="662ba-120">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="662ba-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="662ba-121">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="662ba-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="662ba-122">Category</span><span class="sxs-lookup"><span data-stu-id="662ba-122">Category</span></span>

<span data-ttu-id="662ba-123">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="662ba-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="662ba-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="662ba-124">Affected APIs</span></span>

<span data-ttu-id="662ba-125">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="662ba-125">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
