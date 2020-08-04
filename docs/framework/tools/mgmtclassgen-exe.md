---
title: Mgmtclassgen.exe (Management Strongly Typed Class Generator)
description: Comprendre Mgmtclassgen.exe, le générateur de classes fortement typées de gestion. Cet outil vous permet de générer rapidement une classe managée à liaison anticipée pour une classe WMI.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
ms.openlocfilehash: 89facd4369dad6168e46febd3e34d7f7c235faf0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517293"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Management Strongly Typed Class Generator)
L'outil Management Strongly Typed Class Generator vous permet de générer rapidement une classe managée à liaison anticipée pour une classe WMI (Windows Management Instrumentation) spécifiée. La classe générée simplifie le code à écrire pour accéder à une instance de la classe WMI.  
  
## <a name="syntax"></a>Syntax  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|Argument|Description|  
|--------------|-----------------|  
|*WMIClass*|Classe Windows Management Instrumentation pour laquelle générer une classe managée à liaison anticipée.|  
  
|Option|Description|  
|------------|-----------------|  
|**/l**  *language*|Spécifie le langage à utiliser pour générer la classe managée à liaison anticipée. Vous pouvez spécifier **CS** (C# par défaut), **VB** (Visual Basic), **MC** (C++) ou **JS** (JScript) comme argument de langage.|  
|**/m**  *machine*|Spécifie l'ordinateur auquel se connecter, sur lequel la classe WMI se trouve. La valeur par défaut est l'ordinateur local.|  
|**/n**  *path*|Spécifie le chemin vers l’espace de noms WMI qui contient la classe WMI. Si vous ne spécifiez pas cette option, l’outil génère le code pour *WMIClass* dans l’espace de noms **Root\cimv2** par défaut.|  
|**/o**  *classnamespace*|Spécifie l'espace de noms .NET dans lequel générer la classe de code managé. Si vous ne spécifiez pas cette option, l'outil générera l'espace de noms en fonction de l'espace de noms WMI et du préfixe du schéma. Le préfixe du schéma est la partie du nom de la classe qui précède le trait de soulignement. Par exemple, pour la classe **Win32_OperatingSystem** qui se trouve dans l’espace de noms **Root\cimv2**, l’outil génère la classe dans **ROOT.CIMV2.Win32**.|  
|**/p**  *filepath*|Spécifie le chemin vers le fichier dans lequel le code généré sera enregistré. Si vous ne spécifiez pas cette option, l'outil créera le fichier dans le répertoire actif. Il nomme la classe et le fichier dans lesquels il génère la classe à l’aide de l’argument *WMIClass*. Les noms de la classe et du fichier sont les mêmes que ceux de *WMIClass.* Si *WMIClass* contient un trait de soulignement, l’outil utilise la partie du nom de la classe qui suit le trait de soulignement. Par exemple, si le nom *WMIClass* est au format **Win32_LogicalDisk**, la classe et le fichier générés sont nommés « logicaldisk ». Si un fichier existe déjà, l'outil écrase le fichier existant.|  
|**/pw**  *password*|Définit le mot de passe à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.|  
|**/u**  *user name*|Définit le nom d’utilisateur à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Remarques  
 Mgmtclassgen.exe utilise la méthode <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>. Vous pouvez donc utiliser n'importe quel fournisseur de code personnalisé pour générer le code dans des langages managés autres que C#, Visual Basic et JScript.  
  
 Notez que les classes générées sont liées au schéma pour lequel elles ont été créées. Si le schéma sous-jacent change, vous devez régénérer la classe pour que les modifications effectuées dans le schéma soient prises en compte.  
  
 Le tableau suivant montre la correspondance entre les types Common Information Model (CIM) WMI et les types de données d'une classe générée :  
  
|Type CIM|Type de données dans la classe générée|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Poids**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Unique**|  
|CIM_REAL64|**Double**|  
|CIM_BOOLEAN|**Booléen**|  
|CIM_String|**Chaîne**|  
|CIM_DATETIME|**DateTime** ou **TimeSpan**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Object**|  
|CIM_ARRAY|Tableau des objets mentionnés ci-dessus|  
  
 Notez les comportements suivants lorsque vous générez une classe WMI :  
  
- Il est possible d'utiliser un nom de propriété ou de méthode existant pour une méthode ou une propriété standard publique. Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.  
  
- Le nom d'une propriété ou d'une méthode dans une classe générée peut être un mot clé dans le langage de programmation cible. Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.  
  
- Dans WMI, les qualificateurs sont des modificateurs contenant des informations qui décrivent une classe, une instance, une propriété ou une méthode. WMI utilise des qualificateurs standard, tels que **Read**, **Write** et **Key**, pour décrire une propriété dans une classe générée. Par exemple, une propriété modifiée avec un qualificateur **Read** est définie uniquement avec un accesseur **get** de propriété dans la classe générée. Les propriétés marquées avec un qualificateur **Read** restant en lecture seule, aucun accesseur **set** n’est défini.  
  
- Une propriété numérique peut être modifiée par les qualificateurs **Values** et **ValueMaps** pour indiquer que seules des valeurs autorisées et spécifiées peuvent lui être affectées. Une énumération est générée avec ces qualificateurs **Values** et **ValueMaps**, et la propriété est mappée à l’énumération.  
  
- WMI utilise le singleton de terme pour décrire une classe qui ne peut avoir qu'une seule instance. C'est pourquoi le constructeur sans paramètre d’une classe singleton initialisera la classe à la seule instance de la classe.  
  
- Une classe WMI peut avoir des objets pour propriétés. Lorsque vous générez une classe fortement typée pour ce type de classe WMI, vous devez envisager de générer des classes fortement typées pour les types des propriétés de l’objet incorporé. Cela vous permettra d’accéder aux objets incorporés de manière fortement typée. Il est possible que le code généré ne puisse pas détecter le type de l'objet incorporé. Dans ce cas, un commentaire sera créé dans le code généré pour vous informer de ce problème. Vous pouvez alors modifier le code généré pour typer la propriété vers l'autre classe générée.  
  
- Dans WMI, la valeur du type de données CIM_DATETIME peut représenter soit une date ou une heure spécifique, soit un intervalle de temps. Si la valeur de données représente une date et une heure, le type de données de la classe générée est **DateTime**. Si la valeur de données représente un intervalle de temps, le type de données de la classe générée est **TimeSpan**.  
  
 Vous pouvez également générer une classe fortement typée à l’aide de l’extension de gestion Explorateur de serveurs dans Visual Studio .NET.  
  
 Pour plus d’informations sur WMI, consultez la rubrique **Windows Management Instrumentation** dans la documentation du kit SDK de la plateforme.  
  
## <a name="examples"></a>Exemples  
 La commande suivante génère une classe managée en C# pour la classe WMI **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**. L’outil écrit la classe managée dans le fichier source sous c:\disk.cs dans l’espace de noms **ROOT.CIMV2.Win32**.  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 L'exemple de code suivant montre comment utiliser par programme une classe générée. Tout d'abord, une instance de la classe est énumérée et le chemin est imprimé. Ensuite, une instance de la classe générée à initialiser est créée avec une instance de WMI. `Process` est la classe générée pour **Win32_Process** et `LogicalDisk` est la classe générée pour **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**.  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App
   Public Shared Sub Main()
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [outils](index.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
