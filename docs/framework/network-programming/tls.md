---
title: Meilleures pratiques du protocole TLS (Transport Layer Security) avec .NET Framework
description: Décrit les meilleures pratiques à l’aide du protocole TLS (Transport Layer Security) avec .NET Framework
ms.date: 10/22/2018
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
ms.openlocfilehash: bae6bf6a1a5d87241b619bf024c099c48af6af43
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452680"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Meilleures pratiques du protocole TLS (Transport Layer Security) avec .NET Framework

Le protocole TLS (Transport Layer Security) est une norme industrielle conçue pour aider à protéger la confidentialité des informations communiquées sur Internet. [TLS 1.2](https://tools.ietf.org/html/rfc5246) est une norme qui fournit des améliorations de sécurité par rapport aux versions précédentes. TLS 1.2 sera à terme remplacée par la norme la plus récente [TLS 1.3](https://tools.ietf.org/html/rfc8446) qui est plus rapide et améliore la sécurité. Cet article présente les recommandations visant à sécuriser les applications .NET Framework qui utilisent le protocole TLS.

Pour garantir que les applications .NET Framework restent sécurisées, la version TLS ne doit **pas** être codée en dur. Les applications .NET Framework doivent utiliser la version TLS que prend en charge le système d’exploitation (OS).

Ce document est destiné aux développeurs qui :

- utilisent directement les <xref:System.Net> API (par exemple, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- utilisent directement des clients et des services WCF à l’aide de l’espace de noms <xref:System.ServiceModel?displayProperty=nameWithType>.
- utilisent des rôles de travail et Web [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) pour héberger et exécuter votre application. Consultez la section [Azure Cloud Services](#azure-cloud-services).

Nous vous recommandons :

- cibler .NET Framework 4.7 ou versions ultérieures sur vos applications cibler .NET Framework 4.7.1 ou versions ultérieures sur vos applications WCF
- Ne spécifiez pas la version TLS. Configurez votre code afin de laisser le système d’exploitation décider de la version TLS.
- Effectuez un audit complet du code pour vérifier que vous n’indiquez pas une version SSL ou TLS.

Lorsque votre application permet au système d’exploitation de choisir la version TLS :

- Elle bénéficie automatiquement de nouveaux protocoles ajoutés à l’avenir, tels que TLS 1.3.
- Le système d’exploitation bloque les protocoles qui sont découverts comme n’étant pas sécurisés.

La section [Auditez votre code et apportez-lui des modifications](#audit-your-code-and-make-code-changes) couvre l’audit et la mise à jour de votre code.

Cet article explique comment activer la sécurité maximale disponible pour la version de .NET Framework que votre application cible et sur laquelle elle s’exécute. Lorsqu’une application définit explicitement une version et un protocole de sécurité, il refuse toute autre solution et le comportement de .NET Framework et du système d’exploitation par défaut. Si vous souhaitez que votre application soit en mesure de négocier une connexion TLS 1.2, la définition explicite d’une version antérieure de TLS empêche une connexion TLS 1.2.

Si vous ne pouvez pas éviter de coder en dur une version de protocole, nous vous recommandons vivement de spécifier TLS 1.2. Pour obtenir des conseils sur l’identification et la suppression des dépendances TLS 1,0, téléchargez le livre blanc [résolution du problème tls 1,0](https://www.microsoft.com/download/details.aspx?id=55266) .

WCF prend en charge TLS1.0, 1.1 et 1.2 par la version par défaut dans .NET Framework 4.7. À compter de .NET Framework 4.7.1, WCF passe à la version configurée du système d’exploitation par défaut. Si une application est explicitement configurée avec `SslProtocols.None`, WCF utilise le paramètre par défaut du système d’exploitation lors de l’utilisation du transport NetTcp.

Vous pouvez poser des questions concernant ce document dans le problème GitHub [Meilleures pratiques TLS (Transport Layer Security) avec .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Auditez votre code et apportez-lui des modifications

Pour les applications ASP.NET, inspectez l’élément `<system.web><httpRuntime targetFramework>` de _web.config_ pour vérifier que vous utilisez la version du .NET Framework.

Pour les Windows Forms et d’autres applications, consultez [Comment : cibler une version du .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

Utilisez les sections suivantes pour vérifier que vous n’utilisez pas une version spécifique de SSL ou TLS.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Si votre application cible .NET Framework 4.7 ou versions ultérieures

Les sections suivantes indiquent comment vérifier que vous n’utilisez pas une version spécifique de SSL ou TLS.

### <a name="for-http-networking"></a>Pour la mise en réseau HTTP

<xref:System.Net.ServicePointManager>, à l’aide de .NET Framework 4,7 et versions ultérieures, utilisera le protocole de sécurité par défaut configuré dans le système d’exploitation. Pour obtenir le choix du système d’exploitation par défaut, si possible, ne définissez pas de valeur pour la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>, qui a comme valeur par défaut <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>.

Étant donné que le paramètre <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> oblige l' <xref:System.Net.ServicePointManager> à utiliser le protocole de sécurité par défaut configuré par le système d’exploitation, votre application peut s’exécuter différemment selon le système d’exploitation sur lequel elle est exécutée. Par exemple, Windows 7 SP1 utilise TLS 1,0 alors que Windows 8 et Windows 10 utilisent TLS 1,2.

Le reste de cet article ne s’applique pas lorsque vous ciblez .NET Framework 4.7 ou versions ultérieures pour la mise en réseau HTTP.

### <a name="for-tcp-sockets-networking"></a>Pour la mise en réseau des sockets TCP

<xref:System.Net.Security.SslStream>, à l’aide de .NET Framework 4.7 et versions ultérieures, la valeur par défaut est le système d’exploitation en choisissant le meilleur protocole de sécurité et la meilleure version. Pour obtenir le meilleur système d’exploitation par défaut, si possible, n’utilisez pas les surcharges de méthode de <xref:System.Net.Security.SslStream> qui accepte un paramètre <xref:System.Security.Authentication.SslProtocols> explicite. Sinon, passez <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Nous vous recommandons de ne pas utiliser <xref:System.Security.Authentication.SslProtocols.Default> ; le paramètre `SslProtocols.Default` force l’utilisation de SSL 3.0 /TLS 1.0 et empêche celle de TLS 1.2.

Ne définissez pas une valeur pour la propriété <xref:System.Net.ServicePointManager.SecurityProtocol> (pour la mise en réseau HTTP).

N’utilisez pas les surcharges de méthode de <xref:System.Net.Security.SslStream> qui accepte un paramètre <xref:System.Security.Authentication.SslProtocols> explicite (pour la mise en réseau des sockets TCP). Lorsque vous reciblez votre application vers .NET Framework 4.7 ou versions ultérieures, vous suivez les recommandations de meilleures pratiques.

Le reste de cette rubrique ne s’applique pas lorsque vous ciblez .NET Framework 4.7 ou versions ultérieures pour la mise en réseau des sockets TCP.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Pour le transport TCP de WCF utilisant la sécurité de transport avec des informations d’identification de certificat

WCF utilise la même pile de mise en réseau que le reste de .NET Framework.

Si vous ciblez 4.7.1, WCF est configuré pour autoriser le système d’exploitation à choisir le meilleur protocole de sécurité par défaut, sauf s’il est configuré de manière explicite :

- Dans votre fichier de configuration de l'application.
- **Ou**, dans votre application du code source.

Par défaut, .NET Framework 4.7 et versions ultérieures est configuré pour utiliser TLS 1.2 et autorise les connexions à l’aide de TLS 1.1 ou TLS 1.0. Configurez WCF pour autoriser le système d’exploitation à choisir le meilleur protocole de sécurité en configurant votre liaison pour utiliser <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Sa valeur définie peut être <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` est accessible à partir de <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` est accessible à partir de <xref:System.ServiceModel.NetTcpBinding.Security>.

Si vous utilisez une liaison personnalisée :

- Configurez WCF pour autoriser le système d’exploitation à choisir le meilleur protocole de sécurité en configurant <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> pour utiliser <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Ou** configurez le protocole utilisé avec le chemin d’accès à la configuration `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Si vous n’utilisez **pas** de liaison personnalisée **et** que vous définissez votre liaison WCF à l’aide de la configuration, définissez le protocole utilisé avec le chemin d’accès à configuration `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Pour la sécurité du message WCF avec les informations d’identification de certificat

.NET Framework 4.7 et versions ultérieures utilise par défaut le protocole spécifié dans la propriété <xref:System.Net.ServicePointManager.SecurityProtocol>. Lorsque le `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) est défini sur `true`, WCF choisit le protocole le plus approprié, jusqu’à TLS 1,0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Si votre application cible une version de .NET Framework antérieure à 4.7

Auditez votre code pour vérifier que vous ne définissez pas une version spécifique de SSL ou TLS à l’aide des sections suivantes :

### <a name="for-net-framework-46---462-and-not-wcf"></a>Pour le .NET Framework 4.6 - 4.6.2 et pas pour WCF

Définissez le commutateur `DontEnableSystemDefaultTlsVersions` `AppContext` sur `false`. Consultez [Configuration de la sécurité via des commutateurs AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Pour WCF utilisant .NET Framework 4.6 - 4.6.2, utilisant la sécurité de transport avec des informations d’identification de certificat

Vous devez installer les derniers correctifs du système d’exploitation. Consultez [Mises à jour de sécurité](#security-updates).

L’infrastructure WCF choisit automatiquement le protocole le plus élevé disponible, jusque TLS 1.2, à moins de configurer explicitement une version de protocole. Pour plus d’informations, consultez la section précédente [Pour le transport TCP de WCF utilisant la sécurité de transport avec les informations d’identification de certificat](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Pour .NET Framework 3.5 - 4.5.2 et pas pour WCF

Nous vous recommandons de mettre à niveau votre application avec .NET Framework 4.7 ou versions ultérieures. Si vous ne pouvez pas mettre à niveau, procédez comme suit. À un moment donné dans le futur, votre application peut échouer jusqu'à ce que vous mettiez à niveau avec .NET Framework 4.7 ou versions ultérieures.

Définissez les clés de Registre [SchUseStrongCrypto](#schusestrongcrypto) et [SystemDefaultTlsVersions](#systemdefaulttlsversions) sur 1. Consultez [Configuration de la sécurité via le Registre Windows](#configuring-security-via-the-windows-registry). La version 3.5 de .NET Framework prend en charge l’indicateur `SchUseStrongCrypto` uniquement lorsqu’une valeur explicite de TLS est passée.

Si vous exécutez sur .NET Framework 3.5, vous devez installer un correctif à chaud pour que TLS 1.2 puisse être spécifié par votre programme :

| [KB3154518](https://support.microsoft.com/kb/3154518) | Cumul de fiabilité HR-1605 - Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5.1 sur Windows 7 SP1 et Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Cumul de fiabilité HR-1605 - Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5 sur Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Cumul de fiabilité HR-1605 - Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5 sur Windows 8.1 et Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 1605 correctif cumulatif 3154521 pour .NET Framework 4.5.2 et 4.5.1 sur Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Pour WCF utilisant .NET Framework 3.5 - 4.5.2, utilisant la sécurité de transport TCP avec des informations d’identification de certificat

Ces versions de l’infrastructure WCF sont codées en dur pour utiliser les valeurs SSL 3.0 et TLS 1.0. Ces valeurs ne peuvent pas être modifiées. Vous devez mettre à jour et recibler vers NET Framework 4.6 ou versions ultérieures pour utiliser TLS 1.1 et 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Si votre application cible .NET Framework 3.5

Si vous devez définir explicitement un protocole de sécurité au lieu de laisser .NET ou le système d’exploitation sélectionner le protocole de sécurité, ajoutez `SecurityProtocolTypeExtensions` et `SslProtocolsExtension` énumérations à votre code. `SecurityProtocolTypeExtensions` et `SslProtocolsExtension` incluent des valeurs pour la valeur `Tls12`, `Tls11` et `SystemDefault`. Pour plus d’informations, consultez [prise en charge des versions par défaut du système TLS incluses dans .NET Framework 3,5 sur Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Configuration de la sécurité via des commutateurs AppContext (pour .NET Framework 4.6 ou versions ultérieures)

Les commutateurs [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) décrits dans cette section s’appliquent si votre application cible ou s’exécute sur .NET Framework 4.6 ou versions ultérieures. Par défaut ou s’ils sont définis explicitement, les commutateurs doivent être `false` si possible. Si vous souhaitez configurer la sécurité via un ou les deux commutateurs, ne spécifiez pas de valeur du protocole de sécurité dans votre code ; ceci pourrait écraser le ou les commutateurs.

Les commutateurs ont le même effet, que vous procédiez à la mise en réseau HTTP (<xref:System.Net.ServicePointManager>) ou à la mise en réseau des sockets TCP (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

La valeur de `false` pour `Switch.System.Net.DontEnableSchUseStrongCrypto` incite votre application à utiliser un chiffrement fort. La valeur de `false` pour `DontEnableSchUseStrongCrypto` utilise des protocoles de réseau plus sécurisés (TLS 1.2, TLS 1.1 et TLS 1.0) et bloque les protocoles qui ne sont pas sécurisés. Pour plus d’informations, consultez [L’indicateur SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). La valeur de `true` désactive le chiffrement fort pour votre application.

Si votre application cible .NET Framework 4.6 ou versions ultérieures, la valeur par défaut de ce commutateur est `false`. Il s’agit d’une valeur par défaut sécurisée, que nous vous recommandons. Si votre application s’exécute sur .NET Framework 4.6, mais cible une version antérieure, la valeur par défaut du commutateur est `true`. Dans ce cas, vous devez le définir explicitement sur `false`.

`DontEnableSchUseStrongCrypto` doit uniquement avoir une valeur de `true` si vous avez besoin de vous connecter à d’anciens services qui ne prennent pas en charge le chiffrement fort et ne peuvent pas être mis à niveau.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

La valeur de `false` pour `Switch.System.Net.DontEnableSystemDefaultTlsVersions` incite votre application à autoriser le système d’exploitation à choisir le protocole. Une valeur de `true` incite votre application à utiliser des protocoles sélectionnés par .NET Framework.

Si votre application cible .NET Framework 4.7 ou versions ultérieures, la valeur par défaut de ce commutateur est `false`. Il s’agit d’une valeur par défaut sécurisée, que nous vous recommandons. Si votre application s’exécute sur .NET Framework 4.7 ou versions ultérieures, mais cible une version antérieure, la valeur par défaut du commutateur est `true`. Dans ce cas, vous devez le définir explicitement sur `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

La valeur de `false` pour `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` incite votre application à utiliser la valeur définie dans `ServicePointManager.SecurityProtocols` pour la sécurité du message à l’aide des informations d’identification du certificat. La valeur de `true` utilise le protocole le plus élevé disponible, jusque TLS1.0

Pour les applications ciblant le .NET Framework 4.7 et versions ultérieures, cette valeur par défaut est `false`. Pour les applications ciblant .NET Framework 4.6.2 et versions antérieures, cette valeur par défaut est `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

La valeur de `false` pour `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` incite la configuration par défaut à autoriser le système d’exploitation à choisir le protocole. La valeur de `true` utilise le protocole le plus élevé disponible par défaut, jusque TLS1.2.

Pour les applications ciblant le .NET Framework 4.7.1 et versions ultérieures, cette valeur par défaut est `false`. Pour les applications ciblant .NET Framework 4.7 et versions antérieures, cette valeur par défaut est `true`.

Pour plus d’informations sur les protocoles TLS, consultez [Atténuation : protocoles TLS](../migration-guide/mitigation-tls-protocols.md). Pour plus d'informations sur les commutateurs `AppContext`, consultez [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Configuration de la sécurité via le Registre Windows

> [!WARNING]
> La définition des clés de Registre affecte toutes les applications sur le système. Utilisez cette option uniquement si vous contrôlez entièrement l’ordinateur et pouvez contrôler les modifications apportées au Registre.

Si la définition d’un ou des deux commutateurs `AppContext` n’est pas possible, vous pouvez contrôler les protocoles de sécurité utilisés par votre application avec les clés de Registre Windows décrites dans cette section. Vous ne pouvez peut-être pas utiliser un ou les deux commutateurs `AppContext` si votre application s’exécute sur .NET Framework 4.5.2 ou une version antérieure, ou si vous ne pouvez pas modifier le fichier de configuration. Si vous souhaitez configurer la sécurité avec le registre, ne spécifiez pas de valeur du protocole de sécurité dans votre code ; ceci écrase le paramètre du registre.

Les noms des clés de Registre sont similaires aux noms des commutateurs `AppContext` correspondants, mais sans un `DontEnable` ajouté au nom. Par exemple, le `AppContext` commutateur `DontEnableSchUseStrongCrypto` est la clé de Registre appelée [SchUseStrongCrypto](#schusestrongcrypto).

Ces clés sont disponibles dans toutes les versions .NET Framework pour lesquelles il existe un correctif de sécurité récent. Consultez [Mises à jour de sécurité](#security-updates).

Toutes les clés de Registre décrites ci-dessous ont le même effet, que vous procédiez à la mise en réseau HTTP (<xref:System.Net.ServicePointManager>) ou à la mise en réseau des sockets TCP (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

La clé de Registre `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` a une valeur de type DWORD. La valeur de 1 incite votre application à utiliser un chiffrement fort. Le chiffrement fort utilise des protocoles de réseau plus sécurisés (TLS 1.2, TLS 1.1 et TLS 1.0) et bloque les protocoles qui ne sont pas sécurisés. La valeur de 0 désactive le chiffrement fort. Pour plus d’informations, consultez [L’indicateur SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Si votre application cible .NET Framework 4.6 ou versions ultérieures, la valeur par défaut de cette clé est 1. Il s’agit d’une valeur par défaut sécurisée, que nous vous recommandons. Si votre application s’exécute sur .NET Framework 4.6, mais cible une version antérieure, la valeur par défaut de la clé est 0. Dans ce cas, vous devez le définir explicitement sa valeur sur 1.

Cette clé doit uniquement avoir une valeur de 0 si vous avez besoin de vous connecter à d’anciens services qui ne prennent pas en charge le chiffrement fort et ne peuvent pas être mis à niveau.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

La clé de Registre `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` a une valeur de type DWORD. La valeur de 1 incite votre application à autoriser le système d’exploitation à choisir le protocole. Une valeur de 0 incite votre application à utiliser des protocoles sélectionnés par .NET Framework.

`<VERSION>` doit être v4.0.30319 (pour .NET Framework 4 et versions ultérieures) ou v2.0.50727 (pour .NET Framework 3.5).

Si votre application cible .NET Framework 4.7 ou versions ultérieures, la valeur par défaut de cette clé est 1. Il s’agit d’une valeur par défaut sécurisée, que nous vous recommandons. Si votre application s’exécute sur .NET Framework 4.7 ou versions ultérieures, mais cible une version antérieure, la valeur par défaut de la clé est 0. Dans ce cas, vous devez le définir explicitement sa valeur sur 1.

Pour plus d’informations, consultez [Mise à jour cumulative pour Windows 10 Version 1511 et Windows Server 2016 Technical Preview 4 : 10 mai 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Pour plus d’informations sur .NET Framework 3.5.1, consultez [prise en charge des versions par défaut du système TLS incluses dans .NET Framework 3.5.1 sur Windows 7 SP1 et Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Le fichier _. REG_ suivant définit les clés de Registre et leurs variantes sur leurs valeurs les plus sûres :

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Configuration des protocoles Schannel dans le Registre Windows

Vous pouvez utiliser le Registre pour un contrôle affiné sur les protocoles négociés par votre application client et/ou serveur. La mise en réseau de votre application passe par Schannel (qui est un autre nom pour un [Canal sécurisé](/windows/desktop/SecAuthN/secure-channel). En configurant `Schannel`, vous pouvez configurer le comportement de votre application.

Démarrez avec la clé de Registre `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols`. Sous cette clé, vous pouvez créer toutes les sous-clés dans l’ensemble `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1` et `TLS 1.2`. Sous chacune de ces sous-clés, vous pouvez créer des sous-clés `Client` et/ou `Server`. Sous `Client` et `Server`, vous pouvez créer des valeurs DWORD `DisabledByDefault` (0 ou 1) et `Enabled` (0 ou 0xFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a>L’indicateur SCH_USE_STRONG_CRYPTO

Lorsqu’elle est activée (par défaut, par un commutateur `AppContext`, ou par le Registre Windows), la version .NET Framework utilise l’indicateur `SCH_USE_STRONG_CRYPTO` lorsque votre application demande un protocole de sécurité TLS. L’indicateur `SCH_USE_STRONG_CRYPTO` peut être activé par défaut, avec le commutateur `AppContext` ou avec le Registre. Le système d’exploitation passe de l’indicateur sur `Schannel`pour lui demander de désactiver les algorithmes de chiffrement faibles connus, les suites de chiffrement et les versions du protocole TLS/SSL qui peuvent être également activées pour une meilleure interopérabilité. Pour plus d'informations, consultez les pages suivantes :

- [Canal sécurisé](/windows/desktop/SecAuthN/secure-channel)
- [Structure SCHANNEL_CRED](/windows/win32/api/schannel/ns-schannel-schannel_cred)

L’indicateur `SCH_USE_STRONG_CRYPTO` est également passé sur `Schannel` lorsque vous utilisez explicitement les valeurs énumérées `Tls` (TLS 1.0), `Tls11` ou `Tls12` de <xref:System.Net.SecurityProtocolType> ou <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Mises à jour de sécurité

Les meilleures pratiques dans cet article varient selon les récentes mises à jour de sécurité installées. Ces mises à jour incluent la possibilité d’utiliser les fonctionnalités avancées .NET Framework 4.7 et versions ultérieures. Les récentes mises à jour de sécurité sont importantes si votre application s’exécute sur .NET Framework 4.7 et versions ultérieures (même si elle cible une version antérieure).

Pour mettre à jour .NET Framework afin de permettre au système d’exploitation de choisir la meilleure version de TLS à utiliser, vous devez installer au moins :

- La [Préversion du cumul de qualité .NET Framework d’août 2017](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Ou** le [Cumul de sécurité et de qualité .NET Framework de septembre 2017](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Voir aussi :

- [Versions et dépendances de .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Comment : déterminer les versions du .NET Framework installées](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Prise en charge de TLS 1.2

Pour que votre application négocie TLS 1.2, le système d’exploitation et la version de .NET Framework ont besoin de prendre en charge TLS 1.2.

**Configuration requise pour le système d’exploitation pour la prise en charge de TLS 1.2**

Pour activer ou de réactiver TLS 1.2 et/ou TLS 1.1 sur un système qui les prend en charge, consultez [Paramètres de Registre de TLS (Transport Layer Security)](/windows-server/security/tls/tls-registry-settings).

| **SE** | **Prise en charge de TLS 1.2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Pris en charge, activé par défaut. |
| Windows 8.1<br>Windows Server 2012 R2 | Pris en charge, activé par défaut. |
| Windows 8.0<br>Windows Server 2012 | Pris en charge, activé par défaut. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | Pris en charge, mais non activé par défaut. Consultez la page Web [Paramètres de Registre de TLS (Transport Layer Security)](/windows-server/security/tls/tls-registry-settings) pour plus d’informations sur le mode d’activation de TLS 1.2. |
| Windows Server 2008 | La prise en charge de TLS 1.2 et TLS 1.1 requiert une mise à jour. Consultez [Mettre à jour pour ajouter la prise en charge de TLS 1.1 et TLS 1.2 dans Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Non pris en charge. |

Pour plus d’informations sur les protocoles TLS/SSL activés par défaut sur chaque version de Windows, consultez [Protocoles dans TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**Configuration requise pour la prise en charge de TLS 1.2 avec .NET Framework 3.5**

Ce tableau affiche la mise à jour du système d’exploitation dont vous avez besoin pour prendre en charge TLS 1.2 avec .NET Framework 3.5. Nous vous recommandons d'appliquer toutes les mises à jour du système d’exploitation.

| **SE** | **Mise à jour minimale nécessaire pour prendre en charge TLS 1.2 avec .NET Framework 3.5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Mise à jour cumulative pour Windows 10 Version 1511 et Windows Server 2016 Technical Preview 4 : 10 mai 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5 sur Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5 sur Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 3.5.1 sur Windows 7 SP1 et Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Prise en charge des versions par défaut du système TLS, inclues dans .NET Framework 2.0 SP2 sur Windows Vista SP2 et Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Non pris en charge |

## <a name="azure-cloud-services"></a>Services cloud Azure

Si vous utilisez les rôles de travail et Web [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) pour héberger et exécuter votre application, il existe des considérations dont vous avez besoin pour prendre en compte la prise en charge TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET Framework 4.7 n’est pas installé par défaut sur le système d’exploitation Azure Guest

La dernière version installée de la dernière version 5 de la famille du système d’exploitation Azure Guest (Windows Server 2016) est 4.6.2. Pour connaître les versions de .NET Framework sont installées sur chaque système d’exploitation Azure Guest, consultez la [matrice de compatibilité des versions et du Kit de développement logiciel (SDK) du système d’exploitation invité de Azure Guest](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Si votre application cible une version de .NET Framework qui n’est pas disponible sur la version du système d’exploitation Azure Guest, vous devez l’installer vous-même. Consultez [installer .NET sur les rôles Azure Cloud Services](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Si l’installation de l’infrastructure nécessite un redémarrage, les rôles de service peuvent également redémarrer avant de passer à l’état Prêt.

### <a name="azure-guest-os-registry-settings"></a>Paramètres du Registre du système d’exploitation Azure Guest

L’image Family 5 du système d’exploitation Azure Guest pour [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) possède déjà la clé de Registre `SchUseStrongCrypto` est définie sur une valeur de 1. Pour plus d’informations, consultez [SchUseStrongCrypto](#schusestrongcrypto).

Définissez la clé de Registre [SystemDefaultTlsVersions](#systemdefaulttlsversions) sur 1. Consultez [Configuration de la sécurité via le Registre Windows](#configuring-security-via-the-windows-registry).
