---
title: comportement de marshaling par défaut
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 18282d14540027e4fae4fe152d3867ad8c223c37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181479"
---
# <a name="default-marshaling-behavior"></a>comportement de marshaling par défaut
Le marshaling d'interopérabilité agit sur les règles qui définissent le comportement des données associées aux paramètres de méthode quand elles sont passées de la mémoire managée à la mémoire non managée. Ces règles intégrées contrôlent les activités de marshaling telles que les transformations de types de données, le fait qu’un appelant puisse modifier les données transmises et renvoyer ces modifications à l’appelant, ainsi que les circonstances dans lesquelles le marshaleur fournit des optimisations de performances.  
  
 Cette section aborde les caractéristiques de comportement par défaut du service de marshaling d'interopérabilité. Elle présente des informations détaillées sur le marshaling des tableaux, des types booléens, des types char, des délégués, des classes, des objets, des chaînes et des structures.  
  
> [!NOTE]
> Le marshaling des types génériques n'est pas pris en charge. Pour plus d’informations, consultez [Interopérabilité à l’aide de types génériques](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Gestion de la mémoire avec le marshaleur d'interopérabilité  
 Le marshaleur d'interopérabilité tente toujours de libérer de la mémoire allouée par du code non managé. Ce comportement est conforme aux règles de gestion de mémoire COM, mais pas à celles qui régissent le code C++ natif.  
  
 Vous pouvez créer une confusion si vous anticipez le comportement du C++ natif (aucune libération de mémoire) lors d‘un appel de code non managé qui libère automatiquement de la mémoire pour les pointeurs. Par exemple, l'appel de la méthode non managée suivante à partir d'une DLL C++ ne libère pas automatiquement de la mémoire.  
  
### <a name="unmanaged-signature"></a>Signature non managée  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Toutefois, si vous définissez la méthode comme un prototype d’appel de code non managé, puis remplacez chaque type **BSTR** par un type <xref:System.String> et appelez `MethodOne`, le common language runtime tentera de libérer `b` deux fois. Vous pouvez modifier le comportement de marshaling en utilisant les types <xref:System.IntPtr> plutôt que les types **String**.  
  
 Le runtime utilise toujours la méthode **CoTaskMemFree** pour libérer de la mémoire. Si la mémoire que vous utilisez n’a pas été allouée avec la méthode **CoTaskMemAlloc**, vous devez utiliser un **IntPtr** et libérer la mémoire manuellement à l’aide de la méthode appropriée. De même, vous pouvez éviter la libération automatique de mémoire dans les cas où celle-ci ne doit jamais être libérée, par exemple quand vous utilisez la fonction **GetCommandLine** depuis Kernel32.dll qui retourne un pointeur à la mémoire du noyau. Pour plus d’informations sur la libération manuelle de mémoire, consultez [Mémoires tampons, exemple](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Marshaling par défaut pour les classes  
 Les classes ne peuvent être marshalées que par COM Interop et sont toujours marshalées en tant qu’interfaces. Dans certains cas, l’interface utilisée pour marshaler la classe est appelée interface de classe. Pour plus d’informations sur la substitution de l’interface de classe par une interface de votre choix, consultez [Présentation de l’interface de classe](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Passage de classes à COM  
 Quand une classe managée est passée à COM, le marshaleur d’interopérabilité encapsule automatiquement la classe avec un proxy COM et passe l’interface de classe produite par le proxy à l’appel de méthode COM. Le proxy délègue ensuite tous les appels sur l'interface de classe vers l'objet managé. Le proxy expose également d'autres interfaces qui ne sont pas explicitement implémentées par la classe. Le proxy implémente automatiquement les interfaces telles que **IUnknown** et **IDispatch** pour le compte de la classe.  
  
### <a name="passing-classes-to-net-code"></a>Passage de classes à du code .NET  
 Les coclasses ne sont généralement pas utilisées en tant qu'arguments de méthode dans COM. Au lieu d’une coclasse, c’est une interface par défaut qui est généralement passée.  
  
 Quand une interface est passée dans du code managé, le marshaleur d’interopérabilité est responsable de l’encapsulation de l’interface avec le wrapper approprié et du passage du wrapper à la méthode managée. Savoir quel wrapper utiliser peut s'avérer difficile. Chaque instance d'un objet COM possède un seul et unique wrapper, quel que soit le nombre d'interfaces qu'implémente l'objet. Par exemple, un objet COM qui implémente cinq interfaces différentes n'a qu'un seul wrapper. Le même wrapper expose les cinq interfaces. Si deux instances de l'objet COM sont créées, deux instances du wrapper sont créées.  
  
 Pour que le wrapper conserve le même type durant toute sa durée de vie, le marshaleur d’interopérabilité doit identifier le bon wrapper la première fois qu’une interface exposée par l’objet est passée via le marshaleur. Le marshaleur identifie l’objet en examinant l’une des interfaces implémentées par l’objet.  
  
 Par exemple, le marshaleur détermine que le wrapper de classe doit être utilisé pour encapsuler l’interface qui a été passée dans le code managé. Quand l'interface est initialement passée via le marshaleur, celui-ci vérifie si l'interface provient d'un objet connu. Cette vérification se produit dans deux situations :  
  
- Une interface est implémentée par un autre objet managé qui a été passé à COM à un autre endroit. Le marshaleur peut facilement identifier les interfaces exposées par les objets managés. De plus, il est capable de faire correspondre l'interface avec l'objet managé qui fournit l'implémentation. L'objet managé est ensuite passé à la méthode sans qu'aucun wrapper ne soit nécessaire.  
  
- Un objet qui a déjà été encapsulé implémente l'interface. Afin de déterminer si tel est le cas, le marshaleur interroge l’objet au sujet de son interface **IUnknown** et compare l’interface retournée aux interfaces des autres objets déjà enveloppés. Si l'interface est identique à celle d'un autre wrapper, les objets ont la même identité et le wrapper existant est passé à la méthode.  
  
 Si une interface n’est pas d’un objet connu, le marshaleur effectue ce qui suit :  
  
1. Le marshaleur interroge l’objet au sujet de l’interface **IProvideClassInfo2**. Si celle-ci est fournie, le marshaleur utilise le CLSID retourné à partir d’**IProvideClassInfo2.GetGUID** pour identifier la coclasse fournissant l’interface. Grâce au CLSID, le marshaleur peut localiser le wrapper à partir du Registre si l’assembly a déjà été inscrit.  
  
2. Le marshaleur interroge l’interface au sujet de l’interface **IProvideClassInfo**. Si celle-ci est fournie, le marshaleur utilise l’**ITypeInfo** retourné à partir d’**IProvideClassInfo.GetClassinfo** pour déterminer le CLSID de la classe exposant l’interface. Le marshaleur peut utiliser le CLSID pour localiser les métadonnées du wrapper.  
  
3. Si le marshaleur ne peut toujours pas identifier la classe, il enveloppe l’interface avec une classe wrapper générique appelée **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Marshaling par défaut pour les délégués  
 Un délégué managé est marshalé comme une interface COM ou comme un pointeur fonction, en fonction du mécanisme d’appel :  
  
- Pour un appel de code non managé, un délégué est marshalé en tant que pointeur fonction non managé par défaut.  
  
- Pour COM Interop, un délégué est marshalé comme une interface COM de type **_Delegate** par défaut. L’interface **_Delegate** est définie dans la bibliothèque de types Mscorlib.tlb et contient la méthode <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> qui permet d’appeler la méthode que le délégué référence.  
  
 Le tableau suivant montre les options de marshaling pour le type de données délégué managé. L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les délégués.  
  
|Type d'énumération|Description du format non managé|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Pointeur fonction non managé.|  
|**UnmanagedType.Interface**|Interface de type **_Delegate**, comme défini dans Mscorlib.tlb.|  
  
 Examinez l'exemple de code suivant dans lequel les méthodes de `DelegateTestInterface` sont exportées vers une bibliothèque de types COM. Remarquez que seuls les délégués marqués à l’aide du mot clé **ref** (ou **ByRef**) sont passés en tant que paramètres en entrée/sortie.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a>Représentation d'une bibliothèque de types  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Un pointeur fonction peut être déréférencé, comme n'importe quel autre pointeur fonction non managé.  

Dans cet exemple, quand les deux délégués sont marshalés sous la forme <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, le résultat est un `int` et un pointeur vers un `int`. Comme les types délégués sont marshalés, `int` représente ici un pointeur vers une valeur void (`void*`), qui est l’adresse du délégué en mémoire. En d’autres termes, ce résultat est spécifique des systèmes Windows 32 bits, car `int` représente ici la taille du pointeur de fonction.

> [!NOTE]
> Une référence au pointeur fonction d’un délégué managé compris dans du code non managé n’empêche pas le common language runtime d’effectuer le garbage collection sur l’objet managé.  
  
 Par exemple, le code suivant est incorrect, car la référence à l'objet `cb` passé à la méthode `SetChangeHandler` ne permet pas à `cb` de rester actif au-delà de la durée de vie de la méthode `Test`. Une fois l'objet `cb` collecté, le pointeur fonction passé à `SetChangeHandler` n'est plus valide.  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 Pour compenser les garbage collection inattendus, l'appelant doit s'assurer que l'objet `cb` reste actif aussi longtemps que le pointeur fonction non managé est utilisé. Si vous le souhaitez, vous pouvez faire en sorte que le code non managé informe le code managé quand le pointeur fonction n'est plus utile, comme dans l'exemple suivant.  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a>Marshaling par défaut des types valeur  
 La plupart des types valeur, tels que les nombres entiers et à virgule flottante, sont [blittables](blittable-and-non-blittable-types.md) et ne nécessitent pas de marshaling. D’autres types [non blittables](blittable-and-non-blittable-types.md) ont des représentations différentes selon qu’ils sont en mémoire managée et non managée. De plus, ils nécessitent d’être marshalés. D'autres encore nécessitent une mise en forme explicite au-delà des limites d'interopération.  
  
 Cette section fournit des informations sur les types valeur mis en forme suivants :  
  
- [Types valeur utilisés dans un appel de code non managé](#value-types-used-in-platform-invoke)  
  
- [Types valeur utilisés dans COM Interop](#value-types-used-in-com-interop)  
  
 En plus de décrire les types mis en forme, cette rubrique répertorie les [types valeur système](#system-value-types) qui ont un comportement de marshaling inhabituel.  
  
 Un type mis en forme est un type complexe qui contient des informations qui contrôlent explicitement la disposition de ses membres dans la mémoire. Les informations de disposition des membres sont obtenues à l'aide de l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>. La disposition peut correspondre à l'une des valeurs d'énumération <xref:System.Runtime.InteropServices.LayoutKind> suivantes :  
  
- **LayoutKind.Automatic**  
  
     Indique que le common language runtime est libre de réorganiser les membres du type pour une plus grande efficacité. Toutefois, quand un type valeur est passé à du code non managé, la disposition des membres est prévisible. Si vous tentez de marshaler une telle structure, une exception sera automatiquement levée.  
  
- **LayoutKind.Sequential**  
  
     Indique que les membres du type doivent être disposés dans la mémoire non managée dans le même ordre que celui de la définition de type managé.  
  
- **LayoutKind.Explicit**  
  
     Indique que les membres sont disposés selon le <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fourni avec chaque champ.  
  
### <a name="value-types-used-in-platform-invoke"></a>Types valeur utilisés dans un appel de code non managé  
 Dans l’exemple suivant, les types `Point` et `Rect` fournissent des informations sur la disposition des membres à l’aide de **StructLayoutAttribute**.  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 Quand ils sont marshalés vers du code non managé, ces types mis en forme sont marshalés en tant que structures de style C. Ceci facilite les appels d’API non managées qui possèdent des arguments de structure. Par exemple, les structures `POINT` et `RECT` peuvent être passées à la fonction **PtInRect** de l’API Microsoft Windows de la façon suivante :  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Vous pouvez passer des structures à l'aide de la définition d'appel de code non managé suivante :  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 Le type valeur `Rect` doit être passé par référence, car l'API non managée s'attend à ce qu'un pointeur vers un `RECT` soit passé à la fonction. Le type valeur `Point` est passé par valeur, car l'API non managée s'attend à ce que le `POINT` soit passé à la pile. Cette différence subtile est très importante. Les références sont passées au code non managé comme des pointeurs. Les valeurs sont passées au code non managé sur la pile.  
  
> [!NOTE]
> Quand un type mis en forme est marshalé en tant que structure, seuls les champs du type sont accessibles. Si le type possède des méthodes, des propriétés ou des événements, ceux-ci sont inaccessibles depuis le code non managé.  
  
 Les classes peuvent également être marshalées vers du code non managé en tant que structures de style C, du moment que la disposition des membres est fixe. Les informations de disposition des membres des classes sont également fournies avec l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>. La principale différence entre les types valeur à disposition fixe et les classes à disposition fixe est la manière dont ils sont marshalés vers le code non managé. Les types valeur sont passés par valeur (dans la pile). Toutes les modifications apportées par l'appelé aux membres du type ne sont donc pas vues par l'appelant. Les types référence sont passés par référence (une référence au type est passée sur la pile). Toutes les modifications apportées par l'appelé aux membres d'un type blittable sont donc vues par l'appelant.  
  
> [!NOTE]
> Si un type référence possède des membres de type non blittable, la conversion est requise deux fois : la première fois quand un argument est passé du côté non managé, la seconde fois lors du retour de l'appel. En raison de cette charge mémoire supplémentaire, les paramètres In/Out doivent être explicitement appliqués à un argument si l'appelant veut voir les modifications apportées par l'appelé.  
  
 Dans l’exemple suivant, la classe `SystemTime` a une disposition séquentielle des membres et peut être passée à la fonction **GetSystemTime** de l’API Windows.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 La fonction **GetSystemTime** est définie comme suit :  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 La définition d’appel de code non managé équivalente à **GetSystemTime** se présente comme suit :  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 Notez que l'argument `SystemTime` n'est pas typé comme un argument de référence, car `SystemTime` est une classe et non un type valeur. Contrairement aux types valeur, les classes sont toujours passées par référence.  
  
 L'exemple de code suivant montre une autre classe `Point` qui possède une méthode appelée `SetXY`. Étant donné que le type a une disposition séquentielle, il peut être passé au code non managé et marshalé comme une structure. Toutefois, le membre `SetXY` ne peut pas être appelé depuis du code non managé, même si l'objet est passé par référence.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a>Types valeur utilisés dans COM Interop  
 Les types mis en forme peuvent également être passés aux appels de méthode d'interopérabilité COM. En effet, quand ils sont exportés vers une bibliothèque de types, les types valeur sont convertis automatiquement en structures. Comme dans l'exemple suivant, le type valeur `Point` devient une définition de type (typedef) portant le nom `Point`. Toutes les références au type valeur `Point` situées ailleurs que dans la bibliothèque de types sont remplacées par le typedef `Point`.  
  
 **Représentation de bibliothèque de type**  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 Les règles utilisées pour marshaler des valeurs et des références aux appels de code non managé sont également utilisées lors du marshaling via les interfaces COM. Par exemple, quand une instance du type valeur `Point` est passée de .NET Framework à COM, le `Point` est passé par valeur. Si le type valeur `Point` est passé par référence, un pointeur vers un `Point` est passé sur la pile. Le marshaleur d’interopérabilité ne prend pas en charge les niveaux élevés d’indirection (**Point** \*\*) dans les deux directions.  
  
> [!NOTE]
> Les structures dont la valeur d’énumération <xref:System.Runtime.InteropServices.LayoutKind> est définie sur **Explicit** ne peuvent pas être utilisées dans COM Interop, car la bibliothèque de types exportée ne peut pas exprimer une disposition explicite.  
  
### <a name="system-value-types"></a>Types de valeur système  
 L'espace de noms <xref:System> possède plusieurs types valeur qui représentent la forme boxed de types primitifs de runtime. Par exemple, la structure de type valeur <xref:System.Int32?displayProperty=nameWithType> représente la forme boxed d’**ELEMENT_TYPE_I4**. Au lieu de marshaler ces types en tant que structures, comme le sont les autres types mis en forme, vous les marshalez de la même façon que les types primitifs boxed. **System.Int32** est donc marshalé en tant qu’**ELEMENT_TYPE_I4** et non en tant que structure contenant un seul membre de type **long**. Le tableau suivant répertorie les types valeur de l’espace de noms **System** qui sont des représentations boxed de types primitifs.  
  
|Type de valeur système|Type d'élément|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**ELEMENT_TYPE_BOOLEAN**|  
|<xref:System.SByte?displayProperty=nameWithType>|**ELEMENT_TYPE_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**ELEMENT_TYPE_UI1**|  
|<xref:System.Char?displayProperty=nameWithType>|**ELEMENT_TYPE_CHAR**|  
|<xref:System.Int16?displayProperty=nameWithType>|**ELEMENT_TYPE_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**ELEMENT_TYPE_U2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**ELEMENT_TYPE_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**ELEMENT_TYPE_U4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**ELEMENT_TYPE_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**ELEMENT_TYPE_U8**|  
|<xref:System.Single?displayProperty=nameWithType>|**ELEMENT_TYPE_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**ELEMENT_TYPE_R8**|  
|<xref:System.String?displayProperty=nameWithType>|**ELEMENT_TYPE_STRING**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_I**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_U**|  
  
 Certains autres types valeur de l’espace de noms **System** sont gérés différemment. Étant donné que le code non managé possède déjà des formats bien établis pour ces types, le marshaleur possède des règles spéciales pour les marshaler. Le tableau suivant répertorie les types valeur spéciaux de l’espace de noms **System**, ainsi que le type non managé vers lequel ils sont marshalés.  
  
|Type de valeur système|Type IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**Date**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**Decimales**|  
|<xref:System.Guid?displayProperty=nameWithType>|**Guid**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Le code suivant montre la définition des types non managés **DATE**, **GUID**, **DECIMAL** et **OLE_COLOR** dans la bibliothèque de types Stdole2.  
  
#### <a name="type-library-representation"></a>Représentation d'une bibliothèque de types  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 Le code suivant montre les définitions correspondantes dans l'interface `IValueTypes`.  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a>Représentation d'une bibliothèque de types  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Voir aussi

- [Types blittable et non blittable](blittable-and-non-blittable-types.md)
- [copie et épinglage](copying-and-pinning.md)
- [Marshaling par défaut pour les tableaux](default-marshaling-for-arrays.md)
- [Marshaling par défaut pour les objets](default-marshaling-for-objects.md)
- [Marshaling par défaut pour les chaînes](default-marshaling-for-strings.md)
