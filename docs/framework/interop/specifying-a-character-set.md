---
title: Spécification d'un jeu de caractères
description: Découvrez comment spécifier un jeu de caractères qui utilise l’encodage étroit (ANSI) ou large (Unicode). Vous pouvez également spécifier la sélection automatique du Runtime.
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
ms.openlocfilehash: a4f18431d89343a77ccf2b920edac485e7dcfca3
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282123"
---
# <a name="specifying-a-character-set"></a>Spécification d'un jeu de caractères
Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> contrôle le marshaling des chaînes et détermine de quelle façon l’appel de code non managé recherche des noms de fonction dans une DLL. Cette rubrique décrit ces deux comportements.  
  
 Certaines API exportent deux versions de fonctions qui acceptent des arguments de chaîne : caractères étroits (ANSI) et caractères larges (Unicode). L’API Windows, par exemple, comporte les noms de points d’entrée suivants pour la fonction **MessageBox** :  
  
- **MessageBoxA**  
  
     Fournit un formatage ANSI pour les caractères sur un octet, caractérisé par l’ajout de la lettre A au nom du point d’entrée. Les appels à **MessageBoxA** marshalent toujours les chaînes au format ANSI.  
  
- **MessageBoxW**  
  
     Fournit un formatage Unicode pour les caractères sur deux octets, caractérisé par l’ajout de la lettre W au nom du point d’entrée. Les appels à **MessageBoxW** marshalent toujours les chaînes au format Unicode.  
  
## <a name="string-marshaling-and-name-matching"></a>Marshaling de chaînes et correspondance de noms  
 Le champ `CharSet` accepte les valeurs suivantes :  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi> (valeur par défaut)  
  
- Marshaling de chaînes  
  
     L’appel de code non managé marshale les chaînes de leur format managé (Unicode) au format ANSI.  
  
- Correspondance de noms  
  
     Si le champ <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> a la valeur `true` (valeur par défaut dans Visual Basic), l’appel de code non managé recherche uniquement le nom spécifié. Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.  
  
     Si le champ `ExactSpelling` a la valeur `false` (valeur par défaut en C++ et C#), l’appel de code non managé recherche d’abord l’alias non altéré (**MessageBox**), puis le nom altéré (**MessageBoxA**) si l’alias non altéré est introuvable. Notez que la correspondance de noms ANSI et la correspondance de noms Unicode n’ont pas le même comportement.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Marshaling de chaînes  
  
     L’appel de code non managé copie les chaînes de leur format managé (Unicode) au format Unicode.  
  
- Correspondance de noms  
  
     Si le champ `ExactSpelling` a la valeur `true` (valeur par défaut dans Visual Basic), l’appel de code non managé recherche uniquement le nom spécifié. Par exemple, si vous spécifiez **MessageBox**, l’appel de code non managé recherche **MessageBox** et échoue s’il ne trouve pas de correspondance exacte.  
  
     Si le champ `ExactSpelling` a la valeur `false` (valeur par défaut en C++ et C#), l’appel de code non managé recherche d’abord le nom altéré (**MessageBoxW**), puis l’alias non altéré (**MessageBox**) si le nom altéré est introuvable. Notez que la correspondance de noms Unicode et la correspondance de noms ANSI n’ont pas le même comportement.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- L’appel de code non managé choisit le format Unicode ou le format ANSI au moment de l’exécution, en fonction de la plateforme cible.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Spécification d’un jeu de caractères dans Visual Basic  
 L’exemple suivant déclare la fonction **MessageBox** trois fois, chaque fois avec un comportement de jeu de caractères différent. Vous pouvez spécifier le comportement de jeu de caractères dans Visual Basic en ajoutant le mot clé **Ansi**, **Unicode** ou **Auto** à l’instruction de déclaration.  
  
 Si vous omettez le mot clé de jeu de caractères, comme c’est le cas dans la première instruction de déclaration, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est par défaut défini sur le jeu de caractères ANSI. Dans l’exemple, la deuxième et la troisième instructions spécifient explicitement un jeu de caractères à l’aide d’un mot clé.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Spécification d’un jeu de caractères dans C# et C++  
 Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifie le jeu de caractères sous-jacent au format ANSI ou Unicode. Le jeu de caractères contrôle de quelle manière les arguments de chaîne d’une méthode doivent être marshalés. Spécifiez le jeu de caractères de l’une des manières suivantes :  
  
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
  
 L’exemple suivant montre trois définitions managées de la fonction **MessageBox** attribuées pour spécifier un jeu de caractères. Dans la première définition, du fait de son omission, le champ `CharSet` est par défaut défini sur le jeu de caractères ANSI.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Création de prototypes dans du code managé](creating-prototypes-in-managed-code.md)
- [Exemples d'appel de code non managé](platform-invoke-examples.md)
- [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md)
