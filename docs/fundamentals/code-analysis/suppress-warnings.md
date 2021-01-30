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
# <a name="how-to-suppress-code-analysis-warnings"></a>Comment supprimer des avertissements d’analyse du code

Cet article décrit les différentes façons dont vous pouvez supprimer les avertissements de l’analyse du code lors de la génération de votre application .NET.

> [!TIP]
> Si vous utilisez Visual Studio comme environnement de développement, le menu *ampoule* fournit des options qui génèrent le code pour supprimer les avertissements pour vous. Pour plus d’informations, consultez [Supprimer les violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).

## <a name="disable-the-rule"></a>Désactiver la règle

En désactivant la règle d’analyse du code qui est à l’origine de l’avertissement, vous désactivez la règle pour l’intégralité du fichier ou du projet (en fonction de la portée du [fichier de configuration](configuration-files.md) que vous utilisez). Pour désactiver la règle, définissez sa gravité sur `none` dans le fichier de configuration.

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

Pour plus d’informations sur les niveaux de gravité de la règle, consultez [configurer la gravité](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)de la règle.

## <a name="use-a-preprocessor-directive"></a>Utiliser une directive de préprocesseur

Utilisez une directive [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ou [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) pour supprimer l’avertissement pour une ligne de code spécifique.

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

## <a name="use-the-suppressmessageattribute"></a>Utiliser SuppressMessageAttribute

Vous pouvez utiliser un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> pour supprimer un avertissement dans le fichier source ou dans un fichier de suppression globale pour le projet (*GlobalSuppressions.cs* ou *GlobalSuppressions. vb*). Cet attribut permet de supprimer un avertissement uniquement dans certaines parties de votre projet ou fichier.

Les deux paramètres positionnels requis pour l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut sont la *catégorie* de la règle et l’ID de la *règle*. L’extrait de code suivant passe `"Usage"` et `"CA2200:Rethrow to preserve stack details"` pour ces paramètres.

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

Si vous ajoutez l’attribut au fichier de suppression globale, vous [étendez](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) la suppression au niveau souhaité, par exemple `"member"` . Vous spécifiez l’API dans laquelle l’avertissement doit être supprimé à l’aide de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> propriété.

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

Pour supprimer les avertissements pour le code généré par le compilateur qui n’est pas mappé à une source utilisateur fournie explicitement, vous devez placer l’attribut de suppression dans un fichier de suppression globale. Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par le compilateur :

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>Voir aussi

- [Supprimer les violations (Visual Studio)](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
