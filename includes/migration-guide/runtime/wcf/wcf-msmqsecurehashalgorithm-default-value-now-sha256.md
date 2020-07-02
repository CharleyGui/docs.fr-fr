---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621087"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256. Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas adhérer à la modification en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.7.1|
|Type|Runtime|
