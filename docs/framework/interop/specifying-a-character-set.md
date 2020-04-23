---
title: Spécification d'un jeu de caractères
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 0db1cd8d75b45f6d718168793c873e5867028269
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125171"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="ae57f-102">Spécification d'un jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="ae57f-102">Specifying a Character Set</span></span>
<span data-ttu-id="ae57f-103">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> contrôle le marshaling des chaînes et détermine de quelle façon l’appel de code non managé recherche des noms de fonction dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="ae57f-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="ae57f-104">Cette rubrique décrit ces deux comportements.</span><span class="sxs-lookup"><span data-stu-id="ae57f-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="ae57f-105">Certaines API exportent deux versions de fonctions qui acceptent des arguments de chaîne : caractères étroits (ANSI) et caractères larges (Unicode).</span><span class="sxs-lookup"><span data-stu-id="ae57f-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="ae57f-106">L’API Windows, par exemple, comporte les noms de points d’entrée suivants pour la fonction **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="ae57f-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="ae57f-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="ae57f-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="ae57f-108">Fournit un formatage ANSI pour les caractères sur un octet, caractérisé par l’ajout de la lettre A au nom du point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ae57f-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="ae57f-109">Les appels à **MessageBoxA** marshalent toujours les chaînes au format ANSI.</span><span class="sxs-lookup"><span data-stu-id="ae57f-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="ae57f-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="ae57f-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="ae57f-111">Fournit un formatage Unicode pour les caractères sur deux octets, caractérisé par l’ajout de la lettre W au nom du point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ae57f-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="ae57f-112">Les appels à **MessageBoxW** marshalent toujours les chaînes au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="ae57f-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="ae57f-113">Marshaling de chaînes et correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="ae57f-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="ae57f-114">Le champ `CharSet` accepte les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae57f-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="ae57f-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="ae57f-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="ae57f-116">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="ae57f-116">String marshaling</span></span>  
  
     <span data-ttu-id="ae57f-117">L’appel de code non managé marshale les chaînes de leur format managé (Unicode) au format ANSI.</span><span class="sxs-lookup"><span data-stu-id="ae57f-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="ae57f-118">Correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="ae57f-118">Name matching</span></span>  
  
     <span data-ttu-id="ae57f-119">Si le champ <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> a la valeur `true` (valeur par défaut dans Visual Basic), l’appel de code non managé recherche uniquement le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="ae57f-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="ae57f-120">Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.</span><span class="sxs-lookup"><span data-stu-id="ae57f-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="ae57f-121">Si le champ `ExactSpelling` a la valeur `false` (valeur par défaut en C++ et C#), l’appel de code non managé recherche d’abord l’alias non altéré (**MessageBox**), puis le nom altéré (**MessageBoxA**) si l’alias non altéré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="ae57f-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="ae57f-122">Notez que la correspondance de noms ANSI et la correspondance de noms Unicode n’ont pas le même comportement.</span><span class="sxs-lookup"><span data-stu-id="ae57f-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="ae57f-123">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="ae57f-123">String marshaling</span></span>  
  
     <span data-ttu-id="ae57f-124">L’appel de code non managé copie les chaînes de leur format managé (Unicode) au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="ae57f-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="ae57f-125">Correspondance de noms</span><span class="sxs-lookup"><span data-stu-id="ae57f-125">Name matching</span></span>  
  
     <span data-ttu-id="ae57f-126">Si le champ `ExactSpelling` a la valeur `true` (valeur par défaut dans Visual Basic), l’appel de code non managé recherche uniquement le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="ae57f-126">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="ae57f-127">Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.</span><span class="sxs-lookup"><span data-stu-id="ae57f-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="ae57f-128">Si le champ `ExactSpelling` a la valeur `false` (valeur par défaut en C++ et C#), l’appel de code non managé recherche d’abord le nom altéré (**MessageBoxW**), puis l’alias non altéré (**MessageBox**) si le nom altéré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="ae57f-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="ae57f-129">Notez que la correspondance de noms Unicode et la correspondance de noms ANSI n’ont pas le même comportement.</span><span class="sxs-lookup"><span data-stu-id="ae57f-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="ae57f-130">L’appel de code non managé choisit le format Unicode ou le format ANSI au moment de l’exécution, en fonction de la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="ae57f-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="ae57f-131">Spécification d’un jeu de caractères dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae57f-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="ae57f-132">L’exemple suivant déclare la fonction **MessageBox** trois fois, chaque fois avec un comportement de jeu de caractères différent.</span><span class="sxs-lookup"><span data-stu-id="ae57f-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="ae57f-133">Vous pouvez spécifier le comportement de jeu de caractères dans Visual Basic en ajoutant le mot clé **Ansi**, **Unicode** ou **Auto** à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="ae57f-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="ae57f-134">Si vous omettez le mot clé de jeu de caractères, comme c’est le cas dans la première instruction de déclaration, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est par défaut défini sur le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="ae57f-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="ae57f-135">Dans l’exemple, la deuxième et la troisième instructions spécifient explicitement un jeu de caractères à l’aide d’un mot clé.</span><span class="sxs-lookup"><span data-stu-id="ae57f-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="ae57f-136">Spécification d’un jeu de caractères dans C# et C++</span><span class="sxs-lookup"><span data-stu-id="ae57f-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="ae57f-137">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifie le jeu de caractères sous-jacent au format ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="ae57f-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="ae57f-138">Le jeu de caractères contrôle de quelle manière les arguments de chaîne d’une méthode doivent être marshalés.</span><span class="sxs-lookup"><span data-stu-id="ae57f-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="ae57f-139">Spécifiez le jeu de caractères de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae57f-139">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="ae57f-140">L’exemple suivant montre trois définitions managées de la fonction **MessageBox** attribuées pour spécifier un jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="ae57f-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="ae57f-141">Dans la première définition, du fait de son omission, le champ `CharSet` est par défaut défini sur le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="ae57f-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="ae57f-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae57f-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="ae57f-143">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="ae57f-143">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="ae57f-144">Exemples d’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="ae57f-144">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="ae57f-145">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="ae57f-145">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
