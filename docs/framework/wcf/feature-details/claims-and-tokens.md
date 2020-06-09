---
title: Revendications et jetons
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: cbc97f2224bce640757e1cef88fe325db477cfd7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587025"
---
# <a name="claims-and-tokens"></a>Revendications et jetons

Cette rubrique décrit les différents types de revendications que Windows Communication Foundation (WCF) crée à partir des jetons par défaut qu’il prend en charge.

Vous pouvez examiner les revendications des informations d'identification d'un client à l'aide des classes <xref:System.IdentityModel.Claims.ClaimSet> et <xref:System.IdentityModel.Claims.Claim>. `ClaimSet` contient une collection d'objets `Claim`. Chaque `Claim` contient les membres importants suivants :

- La propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> retourne un URI (Uniform Resource Identifier) qui spécifie le type de revendication qui est fait. Par exemple, un type de revendication peut être une empreinte numérique d’un certificat, auquel cas l’URI est `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint` .

- La propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> retourne un URI qui spécifie le droit de la revendication. Les droits prédéfinis sont regroupés dans la classe <xref:System.IdentityModel.Claims.Rights> (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).

- La propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> retourne la ressource associée à la revendication.

Chaque <xref:System.IdentityModel.Claims.ClaimSet> a également une propriété <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A>, qui représente le <xref:System.IdentityModel.Claims.ClaimSet> de l'`Issuer`.

## <a name="windows-accounts"></a>Comptes Windows

Si les informations d'identification d'un client correspondent à un compte d'utilisateur Windows, le <xref:System.IdentityModel.Claims.ClaimSet> qui en résulte a les valeurs suivantes :

- L'`Issuer` est la valeur retournée par la propriété Windows statique de la classe <xref:System.IdentityModel.Claims.ClaimSet>.

- Les revendications de la collection sont les suivantes :

  - <xref:System.IdentityModel.Claims.Claim> avec une propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dont la valeur est l'identificateur de sécurité (SID), une propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> dont la valeur est `Identity` et une propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> qui retourne la valeur SID réelle. Un SID est une valeur unique que le contrôleur de domaine émet pour chaque utilisateur. Il est utilisé pour identifier l'utilisateur dans ses interactions avec la sécurité Windows.

  - <xref:System.IdentityModel.Claims.Claim> avec une propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dont la valeur est le SID, une propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> dont la valeur est `PossessProperty` et une propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> de la valeur du SID.

  - <xref:System.IdentityModel.Claims.Claim> avec une propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dont la valeur est <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, une propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> dont la valeur est `PossessProperty` et une propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> de la chaîne contenant le nom d'utilisateur (par exemple, « MONORDINATEUR\Bob »).

  - Revendications SID supplémentaires avec propriété <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pour les différents groupes auxquels l'utilisateur appartient.

## <a name="certificates"></a>Certificats

Si les informations d'identification du client sont un certificat, le <xref:System.IdentityModel.Claims.ClaimSet> qui en résulte a les valeurs suivantes :

- Pour les certificats auto-émis, l'`Issuer` est le <xref:System.IdentityModel.Claims.ClaimSet> lui-même. <xref:System.IdentityModel.Claims.ClaimSet> retourne une propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dont la valeur est <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, une propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> dont la valeur est `Identity` et une propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> dont la valeur est un tableau <xref:System.Byte> contenant l'empreinte numérique du certificat.

- Pour un certificat émis par une autorité de certification, l'émetteur est le `ClaimSet` qui représente le certificat de l'autorité de certification.

- Les `Claims` de la collection sont les suivantes :

  - `Claim` dont le `ClaimType` est Empreinte numérique, un `Right` PossessProperty et une `Resource` qui est un tableau d'octets contenant l'empreinte numérique du certificat.

  - Revendications PossessProperty supplémentaires de différents types, notamment X500DistinguishedName, Dns, Name, Upn et Rsa, qui représentent différentes propriétés du certificat. La ressource de la revendication RSA est la clé publique associée au certificat. **Remarque** Lorsque le type d’informations d’identification du client est un certificat que le service mappe à un compte Windows, deux `ClaimSet` objets sont générés. Le premier contient toutes les revendications relatives au compte Windows et le second contient toutes les revendications en rapport avec le certificat.

## <a name="user-namepassword"></a>Nom d'utilisateur/mot de passe

Si les informations d'identification du client sont un nom d'utilisateur/mot de passe (ou équivalent) qui ne correspondent pas à un compte Windows, le `ClaimSet` qui en résulte est émis par la propriété <xref:System.IdentityModel.Claims.ClaimSet.System%2A> statique de la classe `ClaimSet`. `ClaimSet`Contient une `Identity` revendication de type <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> dont la ressource est le nom d’utilisateur fourni par le client. Une revendication correspondante a un `Right` de `PossessProperty`.

## <a name="rsa-keys"></a>Clés RSA

Lorsqu’une clé RSA non associée à un certificat est utilisée, le qui en résulte `ClaimSet` est auto-émis et contient une `Identity` revendication de type <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> dont la ressource est la clé RSA. Une revendication correspondante a un `Right` de `PossessProperty`.

## <a name="saml"></a>SAML

Si le client s'authentifie avec un jeton SAML (Security Assertions Markup Language), le `ClaimSet` qui en résulte est émis par l'entité qui a signé le jeton SAML, souvent le certificat du service STS (Security Token Service) qui a émis le jeton SAML. Le `ClaimSet` contient différentes revendications présentes dans le jeton SAML. Si le jeton SAML contient un `SamlSubject` avec un nom non `null`, une revendication `Identity` de type <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> et une ressource de type <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> sont alors créées.

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Revendications d'identité et ServiceSecurityContext.IsAnonymous

Si aucun des `ClaimSet` objets résultant des informations d’identification du client ne contient une revendication avec un `Right` de `Identity,` , la <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> propriété retourne `true` . En présence d'une ou plusieurs revendications de ce type, la propriété `IsAnonymous` retourne `false`.

## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Gestion des revendications et autorisation avec le modèle d'identité](managing-claims-and-authorization-with-the-identity-model.md)
