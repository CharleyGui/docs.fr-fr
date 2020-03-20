---
title: 'Comment : créer manuellement des wrappers'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: a7818a1c08d8538acfacb22dc270d7ef23a7a582
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181430"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="1e97e-102">Comment : créer manuellement des wrappers</span><span class="sxs-lookup"><span data-stu-id="1e97e-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="1e97e-103">Si vous décidez de déclarer des types COM manuellement dans du code source managé, il est recommandé de démarrer avec un fichier IDL (Interface Definition Language) existant ou une bibliothèque de types existante.</span><span class="sxs-lookup"><span data-stu-id="1e97e-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="1e97e-104">Quand vous ne disposez pas du fichier IDL ou ne pouvez pas générer un fichier de bibliothèque de types, vous pouvez simuler les types COM en créant des déclarations managées et en exportant l'assembly résultant dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="1e97e-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="1e97e-105">Pour simuler des types COM à partir d’une source managée</span><span class="sxs-lookup"><span data-stu-id="1e97e-105">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="1e97e-106">Déclarez les types dans un langage compatible avec la spécification CLS (Common Language Specification) et compilez le fichier.</span><span class="sxs-lookup"><span data-stu-id="1e97e-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="1e97e-107">Exportez l’assembly contenant les types à l’aide de l’outil [Tlbexp.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="1e97e-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="1e97e-108">Utilisez la bibliothèque de types COM exportée comme base pour déclarer des types managés orientés COM.</span><span class="sxs-lookup"><span data-stu-id="1e97e-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="1e97e-109">Pour créer un wrapper RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="1e97e-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="1e97e-110">En supposant que vous disposez d’un fichier IDL ou d’un fichier de bibliothèque de types, choisissez les classes et les interfaces que vous souhaitez inclure dans le wrapper RCW personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1e97e-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="1e97e-111">Vous pouvez exclure tous les types que vous ne souhaitez pas utiliser directement ou indirectement dans votre application.</span><span class="sxs-lookup"><span data-stu-id="1e97e-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="1e97e-112">Créez un fichier source dans un langage conforme à la spécification CLS et déclarez les types.</span><span class="sxs-lookup"><span data-stu-id="1e97e-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="1e97e-113">Consultez [Résumé de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) pour obtenir une description complète du processus de conversion à l’importation.</span><span class="sxs-lookup"><span data-stu-id="1e97e-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="1e97e-114">En effet, quand vous créez un wrapper RCW personnalisé, vous effectuez manuellement l’activité de conversion de type fournie par l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="1e97e-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="1e97e-115">L’exemple fourni dans la section suivante montre les types dans un fichier IDL ou un fichier de bibliothèque de types, et les types correspondants en code C#.</span><span class="sxs-lookup"><span data-stu-id="1e97e-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="1e97e-116">Lorsque les déclarations sont terminées, compilez le fichier comme tout autre code source managé.</span><span class="sxs-lookup"><span data-stu-id="1e97e-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="1e97e-117">Quant aux types importés avec Tlbimp.exe, certains nécessitent des informations supplémentaires, que vous pouvez ajouter directement dans le code.</span><span class="sxs-lookup"><span data-stu-id="1e97e-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="1e97e-118">Pour plus d’informations, consultez [Guide pratique pour modifier des assemblys d’interopérabilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1e97e-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e97e-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1e97e-119">Example</span></span>  
 <span data-ttu-id="1e97e-120">Le code suivant montre un exemple de l’interface `ISATest` et de la classe `SATest` dans IDL, et les types correspondants dans le code source C#.</span><span class="sxs-lookup"><span data-stu-id="1e97e-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="1e97e-121">**Fichier IDL ou fichier bibliothèque de types**</span><span class="sxs-lookup"><span data-stu-id="1e97e-121">**IDL or type library file**</span></span>  
  
```cpp
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="1e97e-122">**Wrapper dans le code source managé**</span><span class="sxs-lookup"><span data-stu-id="1e97e-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e97e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e97e-123">See also</span></span>

- <span data-ttu-id="1e97e-124">[Personnaliser des wrappers RCW (Runtime Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e97e-124">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="1e97e-125">[Types de données COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e97e-125">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="1e97e-126">[Guide pratique pour modifier des assemblys d’interopérabilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e97e-126">[How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="1e97e-127">[Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e97e-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="1e97e-128">Tlbimp.exe (Type Library Importer)</span><span class="sxs-lookup"><span data-stu-id="1e97e-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="1e97e-129">Tlbexp.exe (exportateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="1e97e-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
