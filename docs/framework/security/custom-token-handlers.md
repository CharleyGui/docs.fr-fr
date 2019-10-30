---
title: Gestionnaires de jetons personnalisés
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: ccf794b4c229bbc9b40ae7ec2fd649825122cecf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040554"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="09773-102">Gestionnaires de jetons personnalisés</span><span class="sxs-lookup"><span data-stu-id="09773-102">Custom Token Handlers</span></span>
<span data-ttu-id="09773-103">Cette rubrique traite des gestionnaires de jetons dans WIF et de la façon dont ils sont utilisés pour traiter les jetons.</span><span class="sxs-lookup"><span data-stu-id="09773-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="09773-104">Elle décrit également ce qui est nécessaire pour créer des gestionnaires de jetons personnalisés pour les types de jetons qui ne sont pas pris en charge par défaut dans WIF.</span><span class="sxs-lookup"><span data-stu-id="09773-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="09773-105">Introduction aux gestionnaires de jetons dans WIF</span><span class="sxs-lookup"><span data-stu-id="09773-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="09773-106">WIF s’appuie sur les gestionnaires de jetons de sécurité pour créer, lire, écrire et valider les jetons pour une application par partie de confiance ou un service d’émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="09773-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="09773-107">Les gestionnaires de jetons sont des points d’extensibilité qui vous permettent d’ajouter un gestionnaire de jetons personnalisé dans le pipeline WIF, ou de personnaliser la façon dont un gestionnaire de jeton existant gère les jetons.</span><span class="sxs-lookup"><span data-stu-id="09773-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="09773-108">WIF fournit neuf gestionnaires de jetons de sécurité intégrés qui peuvent être modifiés ou entièrement substitués pour changer la fonctionnalité si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="09773-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="09773-109">Gestionnaires de jetons de sécurité intégrés dans WIF</span><span class="sxs-lookup"><span data-stu-id="09773-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="09773-110">WIF 4.5 comprend neuf classes de gestionnaires de jetons de sécurité qui dérivent de la classe de base abstraite <xref:System.IdentityModel.Tokens.SecurityTokenHandler> :</span><span class="sxs-lookup"><span data-stu-id="09773-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="09773-111">Ajout d’un gestionnaire de jetons personnalisé</span><span class="sxs-lookup"><span data-stu-id="09773-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="09773-112">Certains types de jetons, tels que les jetons SWT (Simple Web Tokens) et JWT (JSON Web Tokens) n’ont pas de gestionnaires de jetons intégrés fournis par WIF.</span><span class="sxs-lookup"><span data-stu-id="09773-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="09773-113">Pour ces types de jetons et d’autres qui n’ont pas de gestionnaire intégré, vous devez effectuer les étapes suivantes pour créer un gestionnaire de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="09773-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="09773-114">Ajout d’un gestionnaire de jetons personnalisé</span><span class="sxs-lookup"><span data-stu-id="09773-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="09773-115">Créez une classe dérivée de <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="09773-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="09773-116">Substituez les méthodes suivantes et fournissez votre propre implémentation :</span><span class="sxs-lookup"><span data-stu-id="09773-116">Override the following methods and provide your own implementation:</span></span>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="09773-117">Ajoutez une référence au nouveau gestionnaire de jetons personnalisé dans le fichier *Web.config* ou *App.config*, dans la section **\<system.identityModel>** qui s’applique à WIF.</span><span class="sxs-lookup"><span data-stu-id="09773-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="09773-118">Par exemple, le balisage de configuration suivant spécifie un nouveau gestionnaire de jetons nommé **MyCustomTokenHandler** qui se trouve dans l’espace de noms **CustomToken**.</span><span class="sxs-lookup"><span data-stu-id="09773-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="09773-119">Notez que si vous fournissez votre propre gestionnaire de jetons pour gérer un type de jeton qui a déjà un gestionnaire de jetons intégré, vous devez ajouter un élément **\<remove>** pour supprimer le gestionnaire par défaut et utiliser votre gestionnaire personnalisé à la place.</span><span class="sxs-lookup"><span data-stu-id="09773-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="09773-120">Par exemple, la configuration suivante remplace le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> par défaut par le gestionnaire de jetons personnalisé :</span><span class="sxs-lookup"><span data-stu-id="09773-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789" />  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
