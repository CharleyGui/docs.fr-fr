---
title: Supprimer les avertissements d’analyse du code
description: Découvrez les différentes façons dont vous pouvez supprimer les violations de l’analyse du code .NET.
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: b08e93089975a59fabfeb0daaf6a2a6454b2c7e8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217252"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="b8907-103">Comment supprimer des avertissements d’analyse du code</span><span class="sxs-lookup"><span data-stu-id="b8907-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="b8907-104">Cet article décrit les différentes façons dont vous pouvez supprimer les avertissements de l’analyse du code lors de la génération de votre application .NET.</span><span class="sxs-lookup"><span data-stu-id="b8907-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="b8907-105">Si vous utilisez Visual Studio comme environnement de développement, le menu *ampoule* fournit des options qui génèrent le code pour supprimer les avertissements pour vous.</span><span class="sxs-lookup"><span data-stu-id="b8907-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="b8907-106">Pour plus d’informations, consultez [Supprimer les violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="b8907-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="b8907-107">Désactiver la règle</span><span class="sxs-lookup"><span data-stu-id="b8907-107">Disable the rule</span></span>

<span data-ttu-id="b8907-108">En désactivant la règle d’analyse du code qui est à l’origine de l’avertissement, vous désactivez la règle pour l’intégralité du fichier ou du projet (en fonction de la portée du [fichier de configuration](configuration-files.md) que vous utilisez).</span><span class="sxs-lookup"><span data-stu-id="b8907-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="b8907-109">Pour désactiver la règle, définissez sa gravité sur `none` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b8907-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="b8907-110">Pour plus d’informations sur les niveaux de gravité de la règle, consultez [configurer la gravité](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)de la règle.</span><span class="sxs-lookup"><span data-stu-id="b8907-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="b8907-111">Utiliser une directive de préprocesseur</span><span class="sxs-lookup"><span data-stu-id="b8907-111">Use a preprocessor directive</span></span>

<span data-ttu-id="b8907-112">Utilisez une directive [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ou [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) pour supprimer l’avertissement pour une ligne de code spécifique.</span><span class="sxs-lookup"><span data-stu-id="b8907-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="b8907-113">Utiliser SuppressMessageAttribute</span><span class="sxs-lookup"><span data-stu-id="b8907-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="b8907-114">Vous pouvez utiliser un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> pour supprimer un avertissement dans le fichier source ou dans un fichier de suppression globale pour le projet (*GlobalSuppressions.cs* ou *GlobalSuppressions. vb*).</span><span class="sxs-lookup"><span data-stu-id="b8907-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="b8907-115">Cet attribut permet de supprimer un avertissement uniquement dans certaines parties de votre projet ou fichier.</span><span class="sxs-lookup"><span data-stu-id="b8907-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="b8907-116">Les deux paramètres positionnels requis pour l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut sont la *catégorie* de la règle et l’ID de la *règle*.</span><span class="sxs-lookup"><span data-stu-id="b8907-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="b8907-117">L’extrait de code suivant passe `"Usage"` et `"CA2200:Rethrow to preserve stack details"` pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="b8907-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

<span data-ttu-id="b8907-118">Si vous ajoutez l’attribut au fichier de suppression globale, vous [étendez](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) la suppression au niveau souhaité, par exemple `"member"` .</span><span class="sxs-lookup"><span data-stu-id="b8907-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="b8907-119">Vous spécifiez l’API dans laquelle l’avertissement doit être supprimé à l’aide de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> propriété.</span><span class="sxs-lookup"><span data-stu-id="b8907-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="b8907-120">Pour supprimer les avertissements pour le code généré par le compilateur qui n’est pas mappé à une source utilisateur fournie explicitement, vous devez placer l’attribut de suppression dans un fichier de suppression globale.</span><span class="sxs-lookup"><span data-stu-id="b8907-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="b8907-121">Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par le compilateur :</span><span class="sxs-lookup"><span data-stu-id="b8907-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="b8907-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8907-122">See also</span></span>

- [<span data-ttu-id="b8907-123">Supprimer les violations (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b8907-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
