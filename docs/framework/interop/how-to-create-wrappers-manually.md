---
title: 'Procédure : créer manuellement des wrappers'
description: Créer manuellement des wrappers de types COM. Utilisez un fichier IDL existant ou une bibliothèque de types, ou créez des déclarations managées et exportez l’assembly vers une bibliothèque de types.
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: 0321e98e6237e54397db7e583546fd69803ab7e1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275955"
---
# <a name="how-to-create-wrappers-manually"></a>Procédure : créer manuellement des wrappers

Si vous décidez de déclarer des types COM manuellement dans du code source managé, il est recommandé de démarrer avec un fichier IDL (Interface Definition Language) existant ou une bibliothèque de types existante. Quand vous ne disposez pas du fichier IDL ou ne pouvez pas générer un fichier de bibliothèque de types, vous pouvez simuler les types COM en créant des déclarations managées et en exportant l'assembly résultant dans une bibliothèque de types.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Pour simuler des types COM à partir d’une source managée  
  
1. Déclarez les types dans un langage compatible avec la spécification CLS (Common Language Specification) et compilez le fichier.  
  
2. Exportez l’assembly contenant les types à l’aide de l’outil [Tlbexp.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3. Utilisez la bibliothèque de types COM exportée comme base pour déclarer des types managés orientés COM.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Pour créer un wrapper RCW (Runtime Callable Wrapper)  
  
1. En supposant que vous disposez d’un fichier IDL ou d’un fichier de bibliothèque de types, choisissez les classes et les interfaces que vous souhaitez inclure dans le wrapper RCW personnalisé. Vous pouvez exclure tous les types que vous ne souhaitez pas utiliser directement ou indirectement dans votre application.  
  
2. Créez un fichier source dans un langage conforme à la spécification CLS et déclarez les types. Consultez [Résumé de la conversion d’une bibliothèque de types en assembly](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) pour obtenir une description complète du processus de conversion à l’importation. En effet, quand vous créez un wrapper RCW personnalisé, vous effectuez manuellement l’activité de conversion de type fournie par l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md). L’exemple fourni dans la section suivante montre les types dans un fichier IDL ou un fichier de bibliothèque de types, et les types correspondants en code C#.  
  
3. Lorsque les déclarations sont terminées, compilez le fichier comme tout autre code source managé.  
  
4. Quant aux types importés avec Tlbimp.exe, certains nécessitent des informations supplémentaires, que vous pouvez ajouter directement dans le code. Pour plus d’informations, consultez [Guide pratique pour modifier des assemblys d’interopérabilité](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).  
  
## <a name="example"></a> Exemple  

 Le code suivant montre un exemple de l’interface `ISATest` et de la classe `SATest` dans IDL, et les types correspondants dans le code source C#.  
  
 **Fichier IDL ou fichier bibliothèque de types**  
  
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
  
 **Wrapper dans le code source managé**  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Personnaliser des wrappers RCW (Runtime Callable Wrapper)](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [Types de données COM](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [Guide pratique pour modifier des assemblys d’interopérabilité](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [Récapitulatif de la conversion d’une bibliothèque de types en assembly](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md)
