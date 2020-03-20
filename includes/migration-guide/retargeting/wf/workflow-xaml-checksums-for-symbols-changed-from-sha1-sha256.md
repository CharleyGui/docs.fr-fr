---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803541"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Les sommes de contrôle XAML de workflow pour les symboles passent de SHA1 à SHA256

|   |   |
|---|---|
|Détails|Pour prendre en charge le débogage avec Visual Studio, l’exécution du workflow génère une somme de contrôle pour un fichier XAML de workflow à l’aide d’un algorithme de hachage. Dans .NET Framework 4.6.2 et les versions antérieures, le hachage de somme de contrôle de flux de travail utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À compter de .NET Framework 4.7, l’algorithme par défaut est passé à SHA1. À compter de .NET Framework 4.8, l’algorithme par défaut est passé à SHA256.|
|Suggestion|Si votre code ne peut pas charger d’instances de workflow ou trouver les symboles appropriés en raison d’un échec de la somme de contrôle, essayez de définir le commutateur <code>AppContext</code>&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; sur true. Dans le code :<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Ou dans la configuration :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.8|
|Type|Reciblage|
