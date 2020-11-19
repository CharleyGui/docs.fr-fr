---
title: Utilisation d’Azure Key Vault pour protéger les secrets au moment de la production
description: Sécurité dans les microservices .NET et les applications web - Azure Key Vault est un excellent moyen de gérer les secrets d’application qui sont entièrement contrôlés par les administrateurs. Les administrateurs peuvent même affecter et révoquer des valeurs de développement sans que les développeurs aient à les gérer.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: d2d3690c0c8787ace6bcdfacbdb612f9ef957b98
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916240"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Utiliser Azure Key Vault pour protéger les secrets au moment de la production

Les secrets stockés comme variables d’environnement ou au moyen de l’outil Secret Manager sont toujours stockés localement sur l’ordinateur et non chiffrés. [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) constitue une option de stockage des secrets plus sûre, offrant un emplacement centralisé et sécurisé pour le stockage des clés et des secrets.

**Azure.Extensions.AspNetCore.Configfiguration.** Le package de secrets permet à une application de ASP.net Core de lire les informations de configuration de Azure Key Vault. Pour commencer à utiliser des secrets à partir d’Azure Key Valut, procédez comme suit :

1. Inscrivez votre application en tant qu’application Azure AD. (L’accès aux coffres de clés est géré par Azure AD.) Pour ce faire, vous pouvez utiliser le portail de gestion Azure.

   Si vous préférez que votre application s’authentifie avec un certificat au lieu d’un mot de passe ou d’une clé secrète client, vous pouvez utiliser l’applet de commande PowerShell [New-AzADApplication](/powershell/module/az.resources/new-azadapplication). Le certificat que vous inscrivez auprès d’Azure Key Vault n’a besoin que de votre clé publique. Votre application utilisera la clé privée.

2. Accordez à l’application inscrite un accès au coffre de clés en créant un principal de service. Pour cela, vous pouvez utiliser les commandes PowerShell suivantes :

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Incluez le coffre de clés en tant que source de configuration dans votre application en appelant la méthode d’extension AzureKeyVaultConfigurationExtensions. AddAzureKeyVault lors de la création d’une <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.

Notez que l’appel d’`AddAzureKeyVault` nécessite l’ID de l’application qui a été inscrite et qui a obtenu l’accès au coffre de clés aux étapes précédentes. Ou bien, vous pouvez tout d’abord exécuter la commande Azure CLI : `az login` , puis utiliser une surcharge de `AddAzureKeyVault` qui prend un DefaultAzureCredential à la place du client.

> [!IMPORTANT]
> Nous vous recommandons d’inscrire Azure Key Vault comme dernier fournisseur de configuration, afin de pouvoir remplacer les valeurs de configuration des fournisseurs précédents.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Utilisation de Azure Key Vault pour protéger les secrets d’application** \
  [https://docs.microsoft.com/azure/architecture/multitenant-identity](/azure/architecture/multitenant-identity-keyvault)

- **Stockage sécurisé des secrets d’application pendant le développement** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Configuration de la protection des données** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Gestion des clés et durée de vie de la protection des données dans ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft.Extensions.Configfiguration** Référentiel GitHub. \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration>

>[!div class="step-by-step"]
>[Précédent](developer-app-secrets-storage.md) 
> [Suivant](../key-takeaways.md)
