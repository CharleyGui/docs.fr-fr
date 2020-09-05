---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497349"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Les surcharges Marshal.SizeOf et Marshal.PtrToStructure provoquent l’arrêt du code dynamique

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5.1, la liaison dynamique aux méthodes <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (via Windows PowerShell, IronPython ou le mot clé dynamic du langage C#, par exemple) peut entraîner des exceptions <code>MethodInvocationExceptions</code>, car de nouvelles surcharges de ces méthodes ont été ajoutées et peuvent être ambiguës pour les moteurs de script.

#### <a name="suggestion"></a>Suggestion

Mettez à jour les scripts pour indiquer clairement quelle surcharge doit être utilisée. Pour cela, castez explicitement les paramètres de type de la méthode en tant que <xref:System.Type>. Cliquez sur [ce lien](https://support.microsoft.com/kb/2909958/) pour plus de détails et d’exemples sur la manière de contourner ce problème.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
