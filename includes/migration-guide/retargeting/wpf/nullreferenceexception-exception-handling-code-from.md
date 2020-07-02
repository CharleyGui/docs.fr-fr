---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614554"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException dans le code de gestion des exceptions à partir de ImageSourceConverter.ConvertFrom

#### <a name="details"></a>Détails

Une erreur dans le code de gestion des exceptions <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> a provoqué la levée d’une exception <xref:System.NullReferenceException?displayProperty=fullName> incorrecte au lieu de l’exception prévue (<xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> ou <xref:System.IO.FileNotFoundException?displayProperty=fullName>). Ce changement corrige cette erreur pour que la méthode lève la bonne exception. <p/>Par défaut, toutes les applications ciblant .NET Framework 4.6.2 et antérieur continuent à lever <xref:System.NullReferenceException?displayProperty=fullName> pour assurer la compatibilité. Les développeurs ciblant .NET Framework 4.7 et ultérieur devraient voir les bonnes exceptions.

#### <a name="suggestion"></a>Suggestion

Les développeurs qui ciblent le .NET Framework 4.7 ou ultérieur et qui préfèrent obtenir l’exception <xref:System.NullReferenceException?displayProperty=fullName> peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de leur application :

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,7         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
