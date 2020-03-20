---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235599"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException dans le code de gestion des exceptions à partir de ImageSourceConverter.ConvertFrom

|   |   |
|---|---|
|Détails|Une erreur dans le code de gestion des exceptions <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> a provoqué la levée d’une exception <xref:System.NullReferenceException?displayProperty=name> incorrecte au lieu de l’exception prévue (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> ou <xref:System.IO.FileNotFoundException?displayProperty=name>). Ce changement corrige cette erreur pour que la méthode lève la bonne exception. <p/>Par défaut, toutes les applications ciblant .NET Framework 4.6.2 et antérieur continuent à lever <xref:System.NullReferenceException?displayProperty=name> pour assurer la compatibilité. Les développeurs ciblant .NET Framework 4.7 et ultérieur devraient voir les bonnes exceptions.|
|Suggestion|Les développeurs qui ciblent le .NET Framework 4.7 ou ultérieur et qui préfèrent obtenir l’exception <xref:System.NullReferenceException?displayProperty=name> peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de leur application :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4,7|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
