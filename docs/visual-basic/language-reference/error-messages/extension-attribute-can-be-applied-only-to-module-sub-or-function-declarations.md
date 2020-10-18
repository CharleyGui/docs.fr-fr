---
title: L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160748"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="3df77-102">BC36550 : l’attribut’extension’ne peut être appliqué qu’aux déclarations’module', 'Sub’ou’Function'</span><span class="sxs-lookup"><span data-stu-id="3df77-102">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="3df77-103">La seule façon d’étendre un type de données dans Visual Basic consiste à définir une méthode d’extension dans un module standard.</span><span class="sxs-lookup"><span data-stu-id="3df77-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="3df77-104">La méthode d’extension peut être une `Sub` procédure ou une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="3df77-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="3df77-105">Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension, `<Extension()>` , à partir de l' <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3df77-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3df77-106">Éventuellement, un module qui contient une méthode d’extension peut être marqué de la même façon.</span><span class="sxs-lookup"><span data-stu-id="3df77-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="3df77-107">Aucune autre utilisation de l’attribut d’extension n’est valide.</span><span class="sxs-lookup"><span data-stu-id="3df77-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="3df77-108">**ID d’erreur :** BC36550</span><span class="sxs-lookup"><span data-stu-id="3df77-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3df77-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3df77-109">To correct this error</span></span>

- <span data-ttu-id="3df77-110">Supprimez l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="3df77-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="3df77-111">Reconcevez votre extension en tant que méthode, définie dans un module englobant.</span><span class="sxs-lookup"><span data-stu-id="3df77-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="3df77-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3df77-112">Example</span></span>

<span data-ttu-id="3df77-113">L’exemple suivant définit une `Print` méthode pour le `String` type de données.</span><span class="sxs-lookup"><span data-stu-id="3df77-113">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a><span data-ttu-id="3df77-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3df77-114">See also</span></span>

- [<span data-ttu-id="3df77-115">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="3df77-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="3df77-116">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="3df77-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="3df77-117">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="3df77-117">Module Statement</span></span>](../statements/module-statement.md)
