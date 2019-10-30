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
# <a name="custom-token-handlers"></a>Gestionnaires de jetons personnalisés
Cette rubrique traite des gestionnaires de jetons dans WIF et de la façon dont ils sont utilisés pour traiter les jetons. Elle décrit également ce qui est nécessaire pour créer des gestionnaires de jetons personnalisés pour les types de jetons qui ne sont pas pris en charge par défaut dans WIF.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Introduction aux gestionnaires de jetons dans WIF  
 WIF s’appuie sur les gestionnaires de jetons de sécurité pour créer, lire, écrire et valider les jetons pour une application par partie de confiance ou un service d’émission de jeton de sécurité (STS). Les gestionnaires de jetons sont des points d’extensibilité qui vous permettent d’ajouter un gestionnaire de jetons personnalisé dans le pipeline WIF, ou de personnaliser la façon dont un gestionnaire de jeton existant gère les jetons. WIF fournit neuf gestionnaires de jetons de sécurité intégrés qui peuvent être modifiés ou entièrement substitués pour changer la fonctionnalité si nécessaire.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Gestionnaires de jetons de sécurité intégrés dans WIF  
 WIF 4.5 comprend neuf classes de gestionnaires de jetons de sécurité qui dérivent de la classe de base abstraite <xref:System.IdentityModel.Tokens.SecurityTokenHandler> :  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Ajout d’un gestionnaire de jetons personnalisé  
 Certains types de jetons, tels que les jetons SWT (Simple Web Tokens) et JWT (JSON Web Tokens) n’ont pas de gestionnaires de jetons intégrés fournis par WIF. Pour ces types de jetons et d’autres qui n’ont pas de gestionnaire intégré, vous devez effectuer les étapes suivantes pour créer un gestionnaire de jetons personnalisé.  
  
#### <a name="adding-a-custom-token-handler"></a>Ajout d’un gestionnaire de jetons personnalisé  
  
1. Créez une classe dérivée de <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2. Substituez les méthodes suivantes et fournissez votre propre implémentation :  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. Ajoutez une référence au nouveau gestionnaire de jetons personnalisé dans le fichier *Web.config* ou *App.config*, dans la section **\<system.identityModel>** qui s’applique à WIF. Par exemple, le balisage de configuration suivant spécifie un nouveau gestionnaire de jetons nommé **MyCustomTokenHandler** qui se trouve dans l’espace de noms **CustomToken**.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Notez que si vous fournissez votre propre gestionnaire de jetons pour gérer un type de jeton qui a déjà un gestionnaire de jetons intégré, vous devez ajouter un élément **\<remove>** pour supprimer le gestionnaire par défaut et utiliser votre gestionnaire personnalisé à la place. Par exemple, la configuration suivante remplace le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> par défaut par le gestionnaire de jetons personnalisé :  
  
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
