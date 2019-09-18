---
title: Autorisation basée sur les revendications utilisant WIF
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: ebf4c28bd2a46c21535b596af22d1fa420d20e71
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045501"
---
# <a name="claims-based-authorization-using-wif"></a>Autorisation basée sur les revendications utilisant WIF
Dans une application de partie de confiance, une autorisation détermine les ressources auxquelles une identité authentifié est autorisé à accéder et les opérations qu'elle est autorisée à exécuter sur ces ressources. Une autorisation incorrecte ou faible entraîne la divulgation d'informations et la falsification de données. Cette rubrique présente les méthodes disponibles pour implémenter une autorisation pour les applications Web ASP.NET qui prennent en charge les revendications et les services qui utilisent Windows Identity Foundation (WIF) et le service d'émission de jetons de sécurité (STS), par exemple, le service de contrôle d'accès (ACS) Microsoft Azure.  
  
## <a name="overview"></a>Présentation  
 Depuis sa version initiale, .NET Framework propose un mécanisme flexible pour implémenter une autorisation. Ce mécanisme est basé sur deux interfaces simples : **IPrincipal** et **IIdentity**. Les implémentations concrètes d’**IIdentity** représentent un utilisateur authentifié. Par exemple, l’implémentation de **WindowsIdentity** représente un utilisateur qui est authentifié par Active Directory et **GenericIdentity** représente un utilisateur dont l’identité est vérifiée par le biais d’une procédure d’authentification personnalisée. Les implémentations concrètes d’**IPrincipal** aident à vérifier les autorisations à l’aide des rôles en fonction du magasin de rôles. Par exemple, **WindowsPrincipal** vérifie si **WindowsIdentity** est membre des groupes Active Directory. Cette vérification est effectuée en appelant la méthode **IsInRole** sur l’interface **IPrincipal**. La vérification de l'accès basé sur les rôles s'appelle le Contrôle d'accès basé sur des rôles (RBAC). Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle](claims-based-authorization-using-wif.md#BKMK_1).  Les revendications peuvent être utilisées pour distribuer des informations sur les rôles pour prendre en charge des mécanismes d'autorisation familiers, basés sur les rôles.  
  
 Les revendications peuvent également être utilisées pour activer des décisions d'autorisation plus compliquées au-delà des rôles. Les revendications peuvent être basées sur quasiment n’importe quelle information relative à l’utilisateur : âge, code postal, pointure, etc. Un mécanisme de contrôle d’accès basé sur des revendications arbitraires est appelé « autorisation basée sur les revendications ». Pour plus d’informations, consultez [Autorisation basée sur les revendications](claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Contrôle d'accès basé sur des rôles  
 RBAC est une méthode d'autorisation dans laquelle les autorisations utilisateur sont gérées et appliquées par une application basée sur les rôles d'utilisateurs. Si un utilisateur a un rôle requis pour exécuter une action, l'accès est autorisé ; sinon, il est refusé.  
  
### <a name="iprincipalisinrole-method"></a>Méthode IPrincipal.IsInRole  
 Pour implémenter l’approche RBAC dans les applications prenant en charge les revendications, utilisez la méthode **IsInRole ()** dans l’interface **IPrincipal** , comme vous le feriez dans des applications qui ne prennent pas en charge les revendications. Il existe plusieurs façons d’utiliser la méthode **IsInRole()**  :  
  
- En appelant explicitement **IPrincipal.IsInRole("Administrator")** . Dans cette approche, les résultats sont une valeur booléenne. Utilisez-les dans vos instructions conditionnelles. Ils peuvent être utilisés arbitrairement n'importe où dans votre code.  
  
- En utilisant la demande de sécurité **PrincipalPermission.Demand()** . Dans cette approche, le résultat est une exception si jamais la demande n'est pas satisfaite. Cela doit répondre à votre stratégie de gestion des exceptions. La levée d’exceptions est beaucoup plus coûteuse du point de vue des performances que le retour de valeurs booléennes. Elle peut être utilisée n'importe où dans votre code.  
  
- En utilisant les attributs déclaratifs **[PrincipalPermission(SecurityAction.Demand, Role = "Administrator")]** . Cette approche est appelée déclarative parce qu'elle est utilisée pour décorer les méthodes. Elle ne peut pas être utilisée dans les blocs de code dans les implémentations de la méthode. Le résultat est une exception si jamais la demande n'est pas satisfaite. Vous devez vous assurer qu'elle répond à votre stratégie de gestion des exceptions.  
  
- En utilisant l’autorisation d’URL, à l’aide de la section **\<authorization>** dans **web.config**. Cette approche convient lorsque vous gérez une autorisation au niveau d'une URL. Il s'agit du niveau le plus simple parmi ceux précédemment mentionnés. L'avantage de cette méthode est que des modifications sont apportées au fichier de configuration, ce qui signifie que le code ne doit pas être compilé pour tirer parti de la modification.  
  
### <a name="expressing-roles-as-claims"></a>Expression de rôles comme revendications  
 Quand la méthode **IsInRole()** est appelée, un contrôle est effectué pour déterminer si l’utilisateur actif détient ce rôle. Dans les applications qui prennent en charge les revendications, le rôle est exprimé par un rôle de revendication qui doit être disponible dans le jeton. Le type de revendication du rôle est exprimé à l'aide de l'URI suivante :  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 Il existe plusieurs façons d'enrichir un jeton avec un type de revendication du rôle :  
  
- **Lors de l’émission de jeton**. Quand un utilisateur est authentifié, la revendication de rôle peut être émise par le STS du fournisseur d’identité ou par un fournisseur de fédération tel que le service de contrôle d’accès (ACS) Microsoft Azure.  
  
- **Transformation des revendications aléatoires en type de rôle de revendications à l’aide de ClaimsAuthenticationManager**. ClaimsAuthorizationManager est un composant qui fournit une partie du WIF. Il permet aux demandes d'être interceptées lorsqu'elles lancent une application, en inspectant des jetons et en les transformant par l'ajout, la modification, ou la suppression de revendications. Pour plus d’informations sur l’utilisation de ClaimsAuthenticationManager pour la transformation des revendications, [consultez Procédure : Implémentez le Access Control basé sur les rôles (RBAC) dans une application ASP.NET prenant en](https://go.microsoft.com/fwlink/?LinkID=247445)charge les revendications à l’aide de WIF et ACS.  
  
- **Mappage des revendications arbitraires à un type de rôle à l’aide de la section de configuration samlSecurityTokenRequirement** : une approche déclarative dans laquelle la transformation des revendications est effectuée à l’aide de la configuration et aucun codage n’est nécessaire.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autorisation basée sur des revendications  
 L'autorisation basée sur des revendications est une approche dans laquelle la décision d'accorder ou de refuser l'accès est basée sur la logique arbitraire qui utilise des données disponibles dans les revendications pour permettre la prise de décision. N'oubliez pas que dans le cas de RBAC, la seule revendication utilisée était la revendication du type de rôle. Une revendication du type de rôle a été utilisée pour vérifier si l'utilisateur appartient au rôle spécifique ou non. Pour illustrer le processus de prise de décision à propos des autorisations à l'aide de l'approche basée sur les revendications, tenez-compte des étapes suivantes :  
  
1. L'application reçoit une demande qui requiert que l'utilisateur soit authentifié.  
  
2. WIF redirige l'utilisateur vers son fournisseur d'identité, une fois qu'il est authentifié, la demande d'application est effectuée avec un jeton de sécurité associé qui représente l'utilisateur contenant les revendications associées. WIF associe ces revendications avec l'entité qui représente l'utilisateur.  
  
3. L'application transmet les revendications au mécanisme de logique de décision. Il peut s'agir d'un code en mémoire, d'un appel à un service Web, d'une requête à une base de données, d'un moteur de règles complexe ou de l'utilisation de ClaimsAuthorizationManager.  
  
4. Le mécanisme de décision calcule les résultats en fonction des revendications.  
  
5. L'accès est accordé si la valeur des résultats est true et refusé si la valeur est false. Par exemple, la règle peut indiquer que l'utilisateur est âgé de plus de 21 ans et habite dans l'état de Washington.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> est utile pour extérioriser la logique de décision pour l'autorisation basée sur les revendications dans vos applications. ClaimsAuthorizationManager est un composant WIF fourni dans le cadre de .NET 4.5. ClaimsAuthorizationManager vous permet d'intercepter des requêtes entrantes et d'implémenter toute logique de votre choix pour prendre des décisions d'autorisation basées sur les revendications entrantes. Cela devient important lorsque la logique d'autorisation doit être modifiée. Dans ce cas, l'utilisation de ClaimsAuthorizationManager n'affecte pas l'intégrité de l'application, réduisant ainsi la probabilité d'une erreur d'application suite à la modification. Pour en savoir plus sur l’utilisation de ClaimsAuthorizationManager pour implémenter le contrôle d’accès basé [sur les revendications, consultez Comment : Implémentez l’autorisation des revendications dans une application ASP.NET prenant en charge](https://go.microsoft.com/fwlink/?LinkID=247446)les revendications à l’aide de WIF et ACS.
