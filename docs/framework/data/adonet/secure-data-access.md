---
title: Sécuriser l'accès aux données
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: 28d3a7d8ccfe2aeafbea0930b8655e41bc45c1a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550779"
---
# <a name="secure-data-access"></a>Sécuriser l'accès aux données
Pour écrire un code ADO.NET sécurisé, vous devez comprendre les mécanismes de sécurité disponibles dans la base de données ou le magasin de données sous-jacent. Vous devez également prendre en compte les implications relatives à la sécurité des autres fonctionnalités ou composants que votre application peut contenir.  
  
## <a name="authentication-authorization-and-permissions"></a>Authentification et autorisations  
 Lorsque vous vous connectez à Microsoft SQL Server, vous pour utiliser l'authentification Windows, également appelée sécurité intégrée, qui utilise l'identité de l'utilisateur Windows actif au lieu de transmettre un ID d'utilisateur et un mot de passe. L'utilisation de l'authentification Windows est hautement recommandée car elle permet de ne pas exposer les informations d'identification de l'utilisateur dans la chaîne de connexion. Si vous ne pouvez pas utiliser l'authentification Windows pour vous connecter à SQL Server, envisagez de créer des chaînes de connexion au moment de l'exécution, en utilisant <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Les informations d'identification utilisées pour l'authentification doivent être traitées différemment en fonction du type d'application. Par exemple, dans une application Windows Forms, il se peut que l'utilisateur soit invité à fournir des informations d'authentification ou que les informations d'identification Windows de l'utilisateur soient utilisées. Toutefois, il est fréquent qu'une application Web accède à des données à l'aide d'informations d'identification fournies par l'application elle-même plutôt que par l'utilisateur.  
  
 Une fois les utilisateurs authentifiés, la portée de leurs actions dépend des autorisations qui leur ont été accordées. Suivez toujours le principe des privilèges minimum et accordez uniquement les autorisations qui sont absolument nécessaires.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Protection des informations de connexion](protecting-connection-information.md)|Décrit les techniques et meilleures pratiques de sécurité permettant de protéger les informations de connexion, telles que l'utilisation d'une configuration protégée pour chiffrer les chaînes de connexion.|  
|[Recommandations pour les stratégies d’accès aux données](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Fournit des recommandations pour l'accès aux données et l'exécution d'opérations de base de données.|  
|[Builders de chaînes de connexion](connection-string-builders.md)|Décrit comment créer des chaînes de connexion à partir de l'entrée de l'utilisateur au moment de l'exécution.|  
|[Vue d'ensemble de la sécurité SQL Server](./sql/overview-of-sql-server-security.md)|Décrit l'architecture de sécurité de SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Commandes paramétrées et injection de code SQL  
 L'utilisation des commandes paramétrées aide à se protéger des attaques par injection de code SQL, dans lesquelles un attaquant « injecte » une commande dans une instruction SQL qui compromet la sécurité sur le serveur. Les commandes paramétrées protègent contre une attaque par injection de code SQL en garantissant que les valeurs reçues à partir d'une source externe sont passées en tant que valeurs uniquement et non pas comme partie intégrante de l'instruction Transact-SQL. Par conséquent, les commandes Transact-SQL insérées dans une valeur ne sont pas exécutées au niveau de la source de données. Au lieu de cela, les valeurs sont évaluées uniquement comme valeurs de paramètre. Outre les avantages relatifs à la sécurité, les commandes paramétrées fournissent une méthode pratique d'organisation des valeurs passées avec une instruction Transact-SQL ou à une procédure stockée.  
  
 Pour plus d'informations sur l'utilisation des commandes paramétrées, voir les ressources répertoriées ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Paramètres DataAdapter](dataadapter-parameters.md)|Décrit comment utiliser des paramètres avec un `DataAdapter`.|  
|[Modification des données avec les procédures stockées](modifying-data-with-stored-procedures.md)|Décrit comment spécifier des paramètres et obtenir une valeur de retour.|  
|[Gestion des autorisations avec les procédures stockées dans SQL Server](./sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Décrit comment utiliser des procédures stockées SQL Server pour encapsuler l'accès aux données.|  
  
## <a name="script-exploits"></a>Attaques de script  
 Une attaque de script est une autre forme d’injection qui utilise des caractères nuisibles insérés dans une page web. Le navigateur ne valide pas les caractères insérés et les traitera dans le cadre de la page.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Vue d’ensemble des attaques de script](/previous-versions/aspnet/w1sw53ds(v=vs.100))|Décrit comment se protéger contre des attaques de script et d'instructions SQL.|  
  
## <a name="probing-attacks"></a>Détection des attaques  
 Les attaquants utilisent souvent des informations incluses dans une exception, telles que le nom de votre serveur, base de données ou table pour organiser une attaque sur votre système. Étant donné que les exceptions peuvent contenir des informations spécifiques relatives à votre application ou à votre source de données, vous pouvez mieux protéger celles-ci en exposant au client seulement les informations indispensables.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Gestion et levée d’exceptions dans .NET](../../../standard/exceptions/index.md)|Décrit les formes de base de la gestion des exceptions structurée autour du bloc try/catch/finally.|  
|[Meilleures pratiques pour les exceptions](../../../standard/exceptions/best-practices-for-exceptions.md)|Décrit les meilleures pratiques de gestion des exceptions.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Protection des sources de données Microsoft Access et Excel  
 Microsoft Access et Microsoft Excel peuvent faire office de magasin de données pour une application ADO.NET quand les exigences de sécurité sont minimales ou inexistantes. Leurs fonctionnalités de sécurité sont efficaces pour la dissuasion, mais ne comptez pas sur elles pour faire plus que décourager des utilisateurs non informés de s’impliquer. Les fichiers de données physiques pour Access et Excel existent sur le système de fichiers et doivent être accessibles à tous les utilisateurs. Cela les rend vulnérables à des attaques susceptibles d'entraîner un vol ou une perte de données car les fichiers peuvent être aisément copiés ou altérés. Lorsqu'une sécurité fiable est requise, utilisez une base de données SQL Server ou une base de données basée sur un autre serveur dans laquelle les fichiers de données physiques ne sont pas lisibles à partir du système de fichiers.  
  
 Pour plus d'informations sur la protection des données Access et Excel, voir les ressources répertoriées ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Considérations et conseils de sécurité pour Access 2007](/previous-versions/office/developer/office-2007/bb421308(v=office.12))|Décrit des techniques de sécurité pour Access 2007, telles que le chiffrement des fichiers, l'administration des mots de passe, la conversion des bases de données vers les nouveaux formats ACCDB et ACCDE, ainsi que l'utilisation d'autres options de sécurité.|  
|[Présentation de l’accès à la sécurité 2010](https://support.office.com/article/Introduction-to-Access-2010-security-CAE6D764-0318-4622-955F-68D9F186D6CA)|Fournit une vue d’ensemble des fonctionnalités de sécurité offertes par Access 2010.|  
## <a name="enterprise-services"></a>Enterprise Services  
 COM + contient son propre modèle de sécurité qui s'appuie sur les comptes Windows NT et l'emprunt d'identité de processus/thread. L'espace de noms <xref:System.EnterpriseServices> fournit des wrappers qui permettent aux applications .NET d'intégrer du code managé avec des services de sécurité COM+ à l'aide de la classe <xref:System.EnterpriseServices.ServicedComponent>.  
  
 Pour plus d'informations, voir la ressource suivante :  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Sécurité basée sur les rôles](/previous-versions/dotnet/netframework-1.1/s6y8k15h(v=vs.71))|Explique comment intégrer du code managé à des services de sécurité COM+.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Interopération avec du code non managé  
 Le .NET Framework permet l'interaction avec du code non managé, y compris des composants COM, des services COM+, des bibliothèques de types externes et de nombreux services de système d'exploitation. Travailler avec du code non managé implique de sortir du périmètre de sécurité pour le code managé. Votre code, ainsi que tout code qui l'appelle, doit disposer de l'autorisation de code non managé (<xref:System.Security.Permissions.SecurityPermission> avec l'indicateur <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> spécifié). Du code non managé peut introduire des vulnérabilités involontaires dans votre application. Par conséquent, vous devez éviter d'interagir avec du code non managé à moins que ce soit absolument nécessaire.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Interopération avec du code non managé](../../interop/index.md)|Contient des rubriques qui décrivent comment exposer les composants COM au .NET Framework et comment exposer les composants .NET Framework à COM.|
|[Interopérabilité COM avancée](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Contient des sujets avancés tels que les assemblys PIA (Primary Interop Assembly), les threads et le marshaling personnalisé.|

## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [Sécurité SQL Server](./sql/sql-server-security.md)
- [Recommandations pour les stratégies d’accès aux données](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Protection des informations de connexion](protecting-connection-information.md)
- [Builders de chaînes de connexion](connection-string-builders.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
