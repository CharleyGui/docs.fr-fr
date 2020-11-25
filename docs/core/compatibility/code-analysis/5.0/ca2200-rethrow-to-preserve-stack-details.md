---
title: 'Modification avec rupture : ca2200 : lever à nouveau pour conserver les détails de la pile'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2200.
ms.date: 09/03/2020
ms.openlocfilehash: 74e169906a8b826328de8d4c5f69c32234c2ce95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761028"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="8c351-103">AVERTISSEMENT ca2200 : lever à nouveau pour conserver les détails de la pile</span><span class="sxs-lookup"><span data-stu-id="8c351-103">Warning CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="8c351-104">La règle d’analyseur de code .NET [ca2200](/visualstudio/code-quality/ca2200) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="8c351-104">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="8c351-105">Il génère un avertissement de génération pour tous les `catch` blocs qui lèvent à nouveau une exception et l’exception est explicitement spécifiée dans l' `throw` instruction.</span><span class="sxs-lookup"><span data-stu-id="8c351-105">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

## <a name="change-description"></a><span data-ttu-id="8c351-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="8c351-106">Change description</span></span>

<span data-ttu-id="8c351-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8c351-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="8c351-108">Plusieurs de ces règles sont activées par défaut, y compris [ca2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="8c351-108">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="8c351-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="8c351-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="8c351-110">Règle ca2200 signale le code où les exceptions sont levées à nouveau et la variable d’exception est spécifiée dans l' `throw` instruction.</span><span class="sxs-lookup"><span data-stu-id="8c351-110">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="8c351-111">Lorsqu’une exception est levée, une partie des informations qu’elle transmet est la trace de la pile.</span><span class="sxs-lookup"><span data-stu-id="8c351-111">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="8c351-112">La trace de la pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception.</span><span class="sxs-lookup"><span data-stu-id="8c351-112">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="8c351-113">Si une exception est levée à nouveau en spécifiant l’exception dans l' `throw` instruction, la trace de la pile redémarre à la méthode actuelle et la liste des appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue.</span><span class="sxs-lookup"><span data-stu-id="8c351-113">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="8c351-114">Pour conserver les informations de trace de la pile d’origine avec l’exception, utilisez l' `throw` instruction sans spécifier l’exception.</span><span class="sxs-lookup"><span data-stu-id="8c351-114">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="8c351-115">L’extrait de code suivant ne génère pas d’avertissement pour la règle ca2200.</span><span class="sxs-lookup"><span data-stu-id="8c351-115">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="8c351-116">Toutefois, la *ligne commentée déclencherait* une violation.</span><span class="sxs-lookup"><span data-stu-id="8c351-116">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a><span data-ttu-id="8c351-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8c351-117">Version introduced</span></span>

<span data-ttu-id="8c351-118">5.0</span><span class="sxs-lookup"><span data-stu-id="8c351-118">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8c351-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8c351-119">Recommended action</span></span>

- <span data-ttu-id="8c351-120">Lever à nouveau les exceptions sans spécifier explicitement l’exception.</span><span class="sxs-lookup"><span data-stu-id="8c351-120">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="8c351-121">Pour plus d’informations, voir [ca2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="8c351-121">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="8c351-122">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="8c351-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="8c351-123">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="8c351-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8c351-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="8c351-124">Affected APIs</span></span>

<span data-ttu-id="8c351-125">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8c351-125">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
