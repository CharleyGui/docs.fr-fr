---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619986"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Les surcharges Marshal.SizeOf et Marshal.PtrToStructure provoquent l’arrêt du code dynamique

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5.1, la liaison dynamique aux méthodes <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (via Windows PowerShell, IronPython ou le mot clé dynamic du langage C#, par exemple) peut entraîner des exceptions <code>MethodInvocationExceptions</code>, car de nouvelles surcharges de ces méthodes ont été ajoutées et peuvent être ambiguës pour les moteurs de script.

#### <a name="suggestion"></a>Suggestion

Mettez à jour les scripts pour indiquer clairement quelle surcharge doit être utilisée. Pour cela, castez explicitement les paramètres de type de la méthode en tant que <xref:System.Type>. Cliquez sur [ce lien](https://support.microsoft.com/kb/2909958/) pour plus de détails et d’exemples sur la manière de contourner ce problème.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|
