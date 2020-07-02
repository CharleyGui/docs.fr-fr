---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614486"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream utilise des API natives pour la décompression

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.2, l’implémentation de la décompression de la classe `T:System.IO.Compression.DeflateStream` a été changée de façon à utiliser des API Windows natives par défaut. En règle générale, s’ensuit une amélioration sensible des performances. Toutes les applications .NET ciblant .NET Framework versions 4.7.2 ou ultérieures utilisent l’implémentation native. Ce changement peut entraîner certaines différences de comportement, notamment les suivantes :

- Les messages d’exception peuvent être différents. Toutefois, le type d’exception levée reste le même.
- Certaines situations particulières, telles que le manque de mémoire pour effectuer une opération, peuvent être traitées différemment.
- Il existe des différences connues pour l’analyse de l’en-tête gzip (remarque : seul `GZipStream` défini pour la décompression est affecté) :
- Les exceptions pendant l’analyse d’en-têtes non valides peuvent être levées à des moments différents.
- L’implémentation native impose que les valeurs de certains indicateurs réservés à l’intérieur de l’en-tête gzip (c’est-à-dire, [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) soient définies en fonction de la spécification ; elle risque donc de lever une exception au lieu d’ignorer les valeurs non valides.

#### <a name="suggestion"></a>Suggestion

Si la décompression avec des API natives a affecté le comportement de votre application, vous pouvez refuser cette fonctionnalité en ajoutant le commutateur `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` à la section `runtime` de votre fichier app.config et en le définissant sur `true` :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
