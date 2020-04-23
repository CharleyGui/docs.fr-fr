---
title: Création de prototypes dans du code managé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
ms.openlocfilehash: 712040c3482b51c4dafe0ee87fdda8cd848fb7fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123619"
---
# <a name="creating-prototypes-in-managed-code"></a>Création de prototypes dans du code managé
Cette rubrique décrit comment accéder aux fonctions non managées et présente plusieurs champs d’attribut qui permettent d’annoter les définitions de méthode dans du code managé. Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](marshaling-data-with-platform-invoke.md).  
  
 Avant de pouvoir accéder à une fonction DLL non managée depuis du code managé, vous devez connaître le nom de la fonction et le nom de la DLL qui l'exporte. Avec ces informations, vous pouvez commencer à écrire la définition managée d'une fonction non managée implémentée dans une DLL. En outre, vous pouvez ajuster la façon dont l'appel de code non managé crée la fonction et marshale les données vers et depuis la fonction.  
  
> [!NOTE]
> Les fonctions de l’API Windows qui allouent une chaîne vous permettent de libérer la chaîne à l’aide d’une méthode telle que `LocalFree`. L'appel de code non managé gère ces paramètres différemment. Pour les appels de code non managé, affectez au paramètre un type `IntPtr` au lieu d'un type `String`. Utilisez les méthodes fournies par la classe <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> pour convertir manuellement le type en chaîne et le libérer manuellement.  
  
## <a name="declaration-basics"></a>Principes de base des déclarations  
 Les définitions managées des fonctions non managées dépendent du langage, comme nous allons le voir dans les exemples suivants. Pour obtenir des exemples de code plus complets, consultez [Exemples d’appel de code non managé](platform-invoke-examples.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Pour appliquer les champs <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> à une déclaration Visual Basic, vous devez utiliser l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> au lieu de l’instruction `Declare`.  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a>Ajustement de la définition  
 Que vous les définissiez explicitement ou non, les champs d'attribut définissent le comportement du code managé. L'appel de code non managé agit selon les valeurs par défaut définies dans les différents champs qui existent sous la forme de métadonnées d'assembly. Vous pouvez modifier ce comportement par défaut en ajustant les valeurs d'un ou plusieurs champs. Dans de nombreux cas, vous utilisez <xref:System.Runtime.InteropServices.DllImportAttribute> pour définir une valeur.  
  
 Le tableau suivant répertorie l'ensemble complet des champs d'attribut qui se rapportent aux appels de code non managé. Pour chaque champ, le tableau inclut la valeur par défaut et un lien vers des informations sur la façon d'utiliser ces champs pour définir des fonctions DLL non managées.  
  
|Champ|Description|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Active ou désactive le mappage ajusté.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Spécifie la convention d'appel à utiliser lors du passage des arguments de méthode. La valeur par défaut est `WinAPI`, ce qui correspond à `__stdcall` pour les plateformes 32 bits Intel.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Contrôle le troncage des noms et la façon dont les arguments de chaîne doivent être marshalés vers la fonction. Par défaut, il s’agit de `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Spécifie le point d'entrée de DLL à appeler.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Détermine si un point d'entrée doit être modifié pour correspondre au jeu de caractères. La valeur par défaut varie en fonction du langage de programmation.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Contrôle si la signature de méthode managée doit être transformée en signature non managée qui retourne un HRESULT et possède un argument supplémentaire [out, retval] pour la valeur de retour.<br /><br /> La valeur par défaut est `true` (la signature ne doit pas être transformée).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Permet à l'appelant d'utiliser la fonction d'API `Marshal.GetLastWin32Error` pour déterminer si une erreur s'est produite lors de l'exécution de la méthode. En Visual Basic, la valeur par défaut est `true` ; en C# et C++, la valeur par défaut est `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Contrôle la levée d'une exception sur un caractère Unicode non mappable converti en un caractère ANSI "?".|  
  
 Pour obtenir des informations de référence détaillées, consultez <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Considérations relatives à la sécurité des appels de code non managé  
 Les membres `Assert`, `Deny` et `PermitOnly` de l’énumération <xref:System.Security.Permissions.SecurityAction> sont appelés *modificateurs de parcours de pile*. Ces membres sont ignorés s'ils sont utilisés comme des attributs déclaratifs sur des déclarations d'appel de code non managé et des instructions Interface Definition Language (IDL) COM.  
  
### <a name="platform-invoke-examples"></a>Exemples d'appel de code non managé  
 Les exemples d'appel de code non managé de cette section illustrent l'utilisation de l'attribut `RegistryPermission` avec les modificateurs de parcours de pile.  
  
 Dans l’exemple suivant, les modificateurs <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny` et `PermitOnly` sont ignorés.  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 Toutefois, le modificateur `Demand` de l'exemple suivant est accepté.  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 Les modificateurs <xref:System.Security.Permissions.SecurityAction> fonctionnent correctement s'ils sont placés sur une classe qui contient (encapsule) l'appel de code non managé.  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 Les modificateurs <xref:System.Security.Permissions.SecurityAction> fonctionnent également correctement dans un scénario d'imbrication dans lequel ils sont placés sur l'appelant de l'appel de code non managé :  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a>Exemples COM Interop  
 Les exemples COM Interop de cette section illustrent l'utilisation de l'attribut `RegistryPermission` avec les modificateurs de parcours de pile.  
  
 Les déclarations d'interface COM Interop ignorent les modificateurs `Assert`, `Deny` et `PermitOnly` de façon similaire aux exemples d'appels de code non managé de la section précédente.  
  
```csharp
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 En outre, le modificateur `Demand` n'est pas accepté dans les scénarios de déclaration d'interface COM Interop, comme illustré dans l'exemple suivant.  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Consommation de fonctions DLL non managées](consuming-unmanaged-dll-functions.md)
- [Spécification d’un point d’entrée](specifying-an-entry-point.md)
- [Spécification d’un jeu de caractères](specifying-a-character-set.md)
- [Exemples d’appel de code non managé](platform-invoke-examples.md)
- [Considérations relatives à la sécurité des appels de code non managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [Identification des fonctions des DLL](identifying-functions-in-dlls.md)
- [Création d’une classe pour contenir des fonctions DLL](creating-a-class-to-hold-dll-functions.md)
- [Appel à une fonction DLL](calling-a-dll-function.md)
