---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887761"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Améliorations de l’accessibilité ASP.NET dans .NET Framework 4.7.1

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.7.1, ASP.NET a amélioré le fonctionnement des contrôles web ASP.NET avec la technologie d’accessibilité de Visual Studio pour une meilleure prise en charge des clients ASP.NET.  Citons notamment les changements suivants :<ul><li>Changements visant à implémenter les modèles d’accessibilité de l’interface utilisateur manquants dans les contrôles, comme la boîte de dialogue Ajouter un champ de l’Assistant de la vue Détails ou la boîte de dialogue Configurer ListView de l’Assistant ListView.</li><li>Changements visant à améliorer l’affichage en mode de contraste élevé, comme l’éditeur de champs du pagineur de données.</li><li>Changements visant à améliorer les expériences de navigation au clavier pour les contrôles, comme la boîte de dialogue Champs de l’Assistant Modifier les champs du pagineur du contrôle DataPager, la boîte de dialogue Configurer ObjectContext ou la boîte de dialogue Configurer la sélection de données de l’Assistant Configurer la source de données.</li></ul>|
|Suggestion|**Accepter ou refuser ces modifications**<br>Pour que le Visual Studio Designer bénéficie de ces changements, il doit s’exécuter sur le cadre .NET 4.7.1 ou plus tard. Pour que l’application web tire parti de ces changements, procédez de l’une des manières suivantes :<ul><li>Installez Visual Studio 2017 15.3 ou une version ultérieure, qui prend en charge les nouvelles fonctionnalités d’accessibilité avec le commutateur AppContext suivant par défaut.</li><li>Refusez les comportements d’accessibilité hérités en ajoutant le commutateur AppContext <code>Switch.UseLegacyAccessibilityFeatures</code> à la section <code>&lt;runtime&gt;</code> du fichier devenv.exe.config et en lui affectant la valeur <code>false</code>, comme indiqué dans l’exemple suivant.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur <code>true</code>.|
|Étendue|Secondaire|
|Version|4.7.1|
|Type|Reciblage|
