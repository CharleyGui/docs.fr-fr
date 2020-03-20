---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859165"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Sommes de contrôle de flux de travail passées de MD5 à SHA1

|   |   |
|---|---|
|Détails|Pour prendre en charge le débogage avec Visual Studio, l’exécution du flux de travail génère une somme de contrôle pour une instance de flux de travail à l’aide d’un algorithme de hachage. Dans .NET Framework 4.6.2 et les versions antérieures, le hachage de somme de contrôle de flux de travail utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À compter de .NET Framework 4.7, l’algorithme est SHA1. Si votre code a rendu persistant ces sommes de contrôle, elles seront incompatibles.|
|Suggestion|Si votre code ne peut pas charger des instances de flux de travail en raison d’un échec de la somme de contrôle, essayez de définir le commutateur <code>AppContext</code>&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; sur true. Dans le code :<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Ou dans la configuration :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4,7|
|Type|Reciblage|
