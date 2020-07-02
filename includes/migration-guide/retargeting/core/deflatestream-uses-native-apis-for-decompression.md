---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614486"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="92f13-101">DeflateStream utilise des API natives pour la décompression</span><span class="sxs-lookup"><span data-stu-id="92f13-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="92f13-102">Détails</span><span class="sxs-lookup"><span data-stu-id="92f13-102">Details</span></span>

<span data-ttu-id="92f13-103">À compter de .NET Framework 4.7.2, l’implémentation de la décompression de la classe `T:System.IO.Compression.DeflateStream` a été changée de façon à utiliser des API Windows natives par défaut.</span><span class="sxs-lookup"><span data-stu-id="92f13-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="92f13-104">En règle générale, s’ensuit une amélioration sensible des performances.</span><span class="sxs-lookup"><span data-stu-id="92f13-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="92f13-105">Toutes les applications .NET ciblant .NET Framework versions 4.7.2 ou ultérieures utilisent l’implémentation native. Ce changement peut entraîner certaines différences de comportement, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="92f13-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="92f13-106">Les messages d’exception peuvent être différents.</span><span class="sxs-lookup"><span data-stu-id="92f13-106">Exception messages may be different.</span></span> <span data-ttu-id="92f13-107">Toutefois, le type d’exception levée reste le même.</span><span class="sxs-lookup"><span data-stu-id="92f13-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="92f13-108">Certaines situations particulières, telles que le manque de mémoire pour effectuer une opération, peuvent être traitées différemment.</span><span class="sxs-lookup"><span data-stu-id="92f13-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="92f13-109">Il existe des différences connues pour l’analyse de l’en-tête gzip (remarque : seul `GZipStream` défini pour la décompression est affecté) :</span><span class="sxs-lookup"><span data-stu-id="92f13-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="92f13-110">Les exceptions pendant l’analyse d’en-têtes non valides peuvent être levées à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="92f13-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="92f13-111">L’implémentation native impose que les valeurs de certains indicateurs réservés à l’intérieur de l’en-tête gzip (c’est-à-dire, [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) soient définies en fonction de la spécification ; elle risque donc de lever une exception au lieu d’ignorer les valeurs non valides.</span><span class="sxs-lookup"><span data-stu-id="92f13-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="92f13-112">Suggestion</span><span class="sxs-lookup"><span data-stu-id="92f13-112">Suggestion</span></span>

<span data-ttu-id="92f13-113">Si la décompression avec des API natives a affecté le comportement de votre application, vous pouvez refuser cette fonctionnalité en ajoutant le commutateur `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` à la section `runtime` de votre fichier app.config et en le définissant sur `true` :</span><span class="sxs-lookup"><span data-stu-id="92f13-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="92f13-114">Nom</span><span class="sxs-lookup"><span data-stu-id="92f13-114">Name</span></span>    | <span data-ttu-id="92f13-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="92f13-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="92f13-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="92f13-116">Scope</span></span>   | <span data-ttu-id="92f13-117">Secondaire</span><span class="sxs-lookup"><span data-stu-id="92f13-117">Minor</span></span>       |
| <span data-ttu-id="92f13-118">Version</span><span class="sxs-lookup"><span data-stu-id="92f13-118">Version</span></span> | <span data-ttu-id="92f13-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="92f13-119">4.7.2</span></span>       |
| <span data-ttu-id="92f13-120">Type</span><span class="sxs-lookup"><span data-stu-id="92f13-120">Type</span></span>    | <span data-ttu-id="92f13-121">Reciblage</span><span class="sxs-lookup"><span data-stu-id="92f13-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="92f13-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="92f13-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
