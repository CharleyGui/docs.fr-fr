---
title: Configurer un serveur proxy lors de l’utilisation du kit de développement logiciel (SDK) Azure pour .NET
description: Utiliser HTTP [S] _PROXY des variables d’environnement pour définir un proxy pour le kit de développement logiciel (SDK) Azure pour .NET
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701121"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a>Configurer un serveur proxy lors de l’utilisation du kit de développement logiciel (SDK) Azure pour .NET

Si votre organisation requiert l’utilisation d’un serveur proxy pour accéder aux ressources Internet, vous devez définir une variable d’environnement avec les informations du serveur proxy pour utiliser le kit de développement logiciel (SDK) Azure pour .NET.  

## <a name="configuration-using-environment-variables"></a>Configuration à l’aide de variables d’environnement

Selon que votre serveur proxy utilise le protocole HTTP ou HTTPs, vous devez définir la variable d’environnement `HTTP_PROXY` ou, `HTTPS_PROXY` respectivement. L’URL du serveur proxy se présente sous la forme `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` dans laquelle la `username:password` combinaison est facultative. Pour obtenir l’adresse IP ou le nom d’hôte, le port et les informations d’identification de votre serveur proxy, consultez votre administrateur réseau.

Les exemples suivants montrent comment définir les variables d’environnement appropriées dans les environnements de l’interface de commande (Windows) et bash (Linux/Mac).  En définissant la variable d’environnement appropriée, le kit de développement logiciel (SDK) Azure pour .NET utilise le serveur proxy lors de l’exécution.

### <a name="cmd"></a>[cmd](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[bash](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
