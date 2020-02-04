---
title: Sécurité d'accès du code
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: c2b6be79855955887988378b9fcffe1891520d68
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980260"
---
# <a name="code-access-security-and-adonet"></a>Sécurité d'accès du code et ADO.NET
Le .NET Framework offre une sécurité basée sur les rôles ainsi qu'une sécurité d'accès du code (CAS, Code Access Security) implémentées à l'aide d'une infrastructure commune fournie par le Common Language Runtime (CLR). Dans l'univers du code non managé, la plupart des applications s'exécutent avec les autorisations de l'utilisateur ou d'une principal de sécurité. C'est pourquoi les systèmes informatiques peuvent être endommagés et des données privées compromises lorsqu'un utilisateur bénéficiant de privilèges élevés exécute des logiciels malveillants ou remplis d'erreurs.  
  
 En revanche, le code managé exécuté dans le .NET Framework inclut une sécurité d'accès du code qui s'applique au code seul. L'autorisation ou l'interdiction pour le code de s'exécuter dépend de son origine et d'autres aspects de son identité, et pas seulement de l'identité de la principal de sécurité. Cela réduit la probabilité que du code managé puisse être utilisé de façon abusive.  
  
## <a name="code-access-permissions"></a>Autorisations d’accès du code  
 Lors de l'exécution du code, ce dernier présente une preuve qui est évaluée par le système de sécurité CLR. Généralement, cette preuve comprend l'origine du code, notamment l'URL, le site, la zone et les signatures numériques qui garantissent l'identité de l'assembly.  
  
 Le CLR permet au code d'effectuer uniquement les opérations pour lesquelles il dispose d'une autorisation. Le code peut demander des autorisations qui lui sont accordées en fonction de la stratégie de sécurité définie par un administrateur.  
  
> [!NOTE]
> Le code s'exécutant dans le CLR ne peut pas s'octroyer d'autorisations à lui-même. Par exemple, un code peut demander et obtenir moins d'autorisations qu'une stratégie de sécurité le prévoit, mais il ne pourra jamais en obtenir plus. Lors de l’octroi d’autorisations, démarrez sans autorisation, puis ajoutez les autorisations les plus restrictives pour la tâche en cours d’exécution. Démarrer avec toutes les autorisations puis en refuser individuellement génère des applications non sécurisées susceptibles de contenir des failles de sécurité involontaires dues à l'octroi de davantage d'autorisations que nécessaire. Pour plus d’informations, consultez Configuration de la [stratégie de sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) et de la gestion des stratégies de [sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Il existe trois types d'autorisations d'accès du code :  
  
- Les `Code access permissions` sont dérivées de la classe <xref:System.Security.CodeAccessPermission>. Des autorisations sont requises pour accéder à des ressources protégées, telles que des fichiers et des variables d'environnement, ainsi que pour effectuer des opérations protégées, telles que l'accès à du code non managé.  
  
- Les `Identity permissions` représentent les caractéristiques qui identifient un assembly. Des autorisations sont octroyées à un assembly sur la base d'une preuve, qui peut consister en différents éléments, tels qu'une signature numérique ou la provenance du code. Les autorisations d'identité dérivent également de la classe de base <xref:System.Security.CodeAccessPermission>.  
  
- Les `Role-based security permissions` sont basées sur le fait qu'une principal de sécurité possède une identité spécifiée ou soit membre d'un rôle particulier. La classe <xref:System.Security.Permissions.PrincipalPermission> permet de procéder à des vérifications d'autorisations déclaratives et impératives par rapport à la principal de sécurité active.  
  
 Pour déterminer si le code est autorisé à accéder à une ressources ou effectuer une opération, le système de sécurité du runtime parcourt la pile des appels, en comparant les autorisations de chaque appelant à l'autorisation faisant l'objet d'une demande. Si un appelant dans la pile des appels ne possède pas l'autorisation demandée, une exception <xref:System.Security.SecurityException> est levée et l'accès est refusé.  
  
### <a name="requesting-permissions"></a>Demande d’autorisations  
 Les demandes d'autorisations ont pour but d'indiquer au runtime les autorisations dont votre application a besoin pour s'exécuter et de garantir que seules les autorisations requises lui sont octroyées. Par exemple, si votre application doit écrire des données sur le disque local, elle nécessite <xref:System.Security.Permissions.FileIOPermission>. Si cette autorisation n'a pas été accordée, l'application échoue lorsqu'elle tente d'écrire sur le disque. Cependant, si l'application demande `FileIOPermission` et que cette autorisation lui a été refusée, l'application génère l'exception dès le départ et ne se charge pas.  
  
 Dans un scénario dans lequel l'application a seulement besoin de lire des données du disque, vous pouvez demander à ce qu'aucune autorisation d'accès en écriture ne lui soit jamais octroyée. En cas de bogue ou d'attaque malveillante, votre code ne peut pas altérer les données sur lesquelles il opère. Pour plus d’informations, consultez [demande d’autorisations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Sécurité basée sur les rôles et sécurité d'accès du code (CAS)  
 L'implémentation de la sécurité basée sur les rôles et de la sécurité d'accès du code (CAS) améliore la sécurité globale de votre application. La sécurité basée sur les rôles peut utiliser un compte Windows ou une identité personnalisée, en mettant à la disposition du thread actuel des informations sur la principal de sécurité. Par ailleurs, les applications doivent souvent accorder l'accès aux données et aux ressources en fonction des informations d'identification fournies par l'utilisateur. Généralement, ces applications vérifient le rôle de l'utilisateur afin de lui donner accès aux ressources correspondant à ce rôle.  
  
 La sécurité basée sur les rôles permet à un composant d'identifier les utilisateurs actuels et leurs rôles associés au moment de l'exécution. Ces informations sont ensuite mappées à l'aide d'une stratégie de sécurité d'accès du code pour déterminer le jeu d'autorisations octroyées au moment de l'exécution. Pour un domaine d'application spécifié, l'hôte peut modifier la stratégie de sécurité basée sur les rôles par défaut et définir une principal de sécurité par défaut qui représente un utilisateur et les rôles qui lui sont associés.  
  
 Le CLR utilise des autorisations pour mettre en œuvre son mécanisme destiné à imposer des restrictions sur du code managé. Les autorisations de sécurité basées sur les rôles fournissent un mécanisme permettant de savoir si un utilisateur (ou l'agent qui agit en son nom) possède une identité particulière ou est membre d'un rôle spécifié. Pour plus d’informations, consultez [autorisations de sécurité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 En fonction du type d'application en cours de construction, vous devez également envisager d'implémenter des autorisations basées sur les rôles dans la base de données. Pour plus d’informations sur la sécurité basée sur les rôles dans SQL Server, consultez [SQL Server sécurité](./sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Assemblies  
 Les assemblys constituent l'unité fondamentale dans le déploiement, le contrôle de version, la portée d'activation et les autorisations de sécurité d'une application .NET Framework. Ils fournissent une collection de types et de ressources qui sont générés pour fonctionner ensemble et former une unité logique de fonctionnalités. Pour le CLR, un type n'existe pas en dehors du contexte d'un assembly. Pour plus d’informations sur la création et le déploiement d’assemblys, consultez [programmation avec des assemblys](../../../standard/assembly/program.md).  
  
### <a name="strong-naming-assemblies"></a>Attribution d'un nom fort à des assemblys  
 Un nom fort, ou signature numérique, est constitué de l'identité de l'assembly (son simple nom textuel, son numéro de version et des informations de culture, le cas échéant) ainsi que d'une clé publique et d'une signature numérique. La signature numérique est générée à partir un fichier d'assembly à l'aide de la clé privée correspondante. Le fichier d'assembly contient le manifeste d'assembly, qui à son tour comporte les noms et les hachages de tous les fichiers qui composent l'assembly.  
  
 L'attribution d'un nom fort à un assembly donne à une application ou un composant une identité unique que d'autres logiciels peuvent utiliser pour s'y référer explicitement. L'attribution de noms forts aux assemblys les protège contre des falsifications par un assembly contenant un code hostile. Elle garantit également la cohérence du contrôle des versions d'un composant. Vous devez attribuer un nom fort aux assemblys qui seront déployés sur le cache GAC (Global Assembly Cache). Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Confiance partielle dans ADO.NET 2.0  
 Dans ADO.NET 2.0, le fournisseur de données .NET Framework pour SQL Server , le fournisseur de données .NET Framework pour OLE DB, le fournisseur de données .NET Framework pour ODBC et le fournisseur de données .NET Framework pour Oracle peuvent tous s'exécuter dans des environnements bénéficiant d'une confiance partielle. Dans les mises en production précédentes du .NET Framework, seul <xref:System.Data.SqlClient> était pris en charge dans des applications ne bénéficiant pas d’une confiance totale.  
  
 Au minimum, une application avec confiance partielle utilisant le fournisseur SQL Server doit disposer d'autorisations d'exécution et de l'objet <xref:System.Data.SqlClient.SqlClientPermission>.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Propriétés d'attribut d'autorisation pour la confiance partielle  
 Pour des scénarios de confiance partielle, vous pouvez utiliser des membres de l'objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute> pour restreindre davantage les capacités disponibles pour le fournisseur de données .NET Framework pour SQL Server.  
  
 Le tableau suivant répertorie les propriétés de l'objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute> disponibles et leurs descriptions :  
  
|Propriété d'attribut d'autorisation|Description|  
|-----------------------------------|-----------------|  
|`Action`|Obtient ou définit une action de sécurité. Hérité de l'objet <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Active ou désactive l'utilisation d'un mot de passe vide dans une chaîne de connexion. Les valeurs valides sont `true` (pour activer l'utilisation des mots de passe vides) et `false` (pour la désactiver). Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identifie une chaîne de connexion autorisée. Plusieurs chaînes de connexion peuvent être identifiées. **Remarque :**  N’incluez pas d’ID utilisateur ou de mot de passe dans votre chaîne de connexion. Dans cette version, vous ne pouvez pas modifier les restrictions liées à la chaîne de connexion à l'aide de l'outil de configuration .NET Framework. <br /><br /> Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Identifie les paramètres de chaîne de connexion autorisés et non autorisés. Les paramètres de chaîne de connexion sont identifiés sous la forme *\<nom de paramètre > =* . Il est possible de spécifier plusieurs paramètres, délimités par un point-virgule (;). **Remarque :**  Si vous ne spécifiez pas `KeyRestrictions`, mais que vous affectez à `KeyRestrictionBehavior` propriété la valeur `AllowOnly` ou `PreventUsage`, aucun paramètre de chaîne de connexion supplémentaire n’est autorisé. Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifie les paramètres de chaîne de connexion comme étant les seuls paramètres supplémentaires autorisés (`AllowOnly`) ou identifie les paramètres supplémentaires qui ne sont pas autorisés (`PreventUsage`). `AllowOnly` est la valeur par défaut. Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Obtient un identificateur unique pour cet attribut lors de l'implémentation dans une classe dérivée. Hérité de l'objet <xref:System.Attribute>.|  
|`Unrestricted`|Indique si une autorisation illimitée à la ressource est déclarée. Hérité de l'objet <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Syntaxe de ConnectionString  
 L'exemple suivant illustre l'utilisation de l'élément `connectionStrings` d'un fichier de configuration pour n'autoriser l'utilisation que d'une seule chaîne de connexion spécifique. Consultez [chaînes de connexion](connection-strings.md) pour plus d’informations sur le stockage et la récupération des chaînes de connexion à partir des fichiers de configuration.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Syntaxe de KeyRestrictions  
 L’exemple suivant active la même chaîne de connexion, active l’utilisation des options de chaîne de connexion `Encrypt` et `Packet Size`, mais restreint l’utilisation de toute autre option de chaîne de connexion.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior avec la syntaxe de PreventUsage  
 L'exemple suivant active la même chaîne de connexion et autorise tous les autres paramètres de connexion à l'exception de `User Id`, `Password` et `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior avec la syntaxe de AllowOnly  
 L'exemple suivant active deux chaînes de connexion qui contiennent également des paramètres `Initial Catalog`, `Connection Timeout`, `Encrypt` et `Packet Size`. L'utilisation de tous les autres paramètres de chaîne de connexion est restreinte.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Activation de confiance partielle avec un jeu d'autorisations personnalisé  
 Pour activer l'utilisation d'autorisations <xref:System.Data.SqlClient> pour une zone particulière, un administrateur système doit créer un jeu d'autorisations personnalisé et le définir comme jeu d'autorisations pour une zone particulière. Les jeux d'autorisations par défaut, tels que `LocalIntranet`, ne peuvent pas être modifiés. Par exemple, pour inclure <xref:System.Data.SqlClient> autorisations pour du code qui a un <xref:System.Security.Policy.Zone> de `LocalIntranet`, un administrateur système peut copier le jeu d’autorisations pour `LocalIntranet`, le renommer en « CustomLocalIntranet », ajouter les autorisations <xref:System.Data.SqlClient>, importer le jeu d’autorisations CustomLocalIntranet à l’aide de [Caspol. exe (outil de stratégie de sécurité d’accès du code)](../../tools/caspol-exe-code-access-security-policy-tool.md)et définir le jeu d’autorisations de `LocalIntranet_Zone` sur CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Exemple de jeu d'autorisations  
 Voici un exemple de jeu d'autorisations destiné au fournisseur de données .NET Framework pour SQL Serveur dans un scénario à confiance partielle. Pour plus d’informations sur la création de jeux d’autorisations personnalisés, consultez [Configuration des jeux d’autorisations à l’aide de Caspol. exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Vérification de l'accès du code ADO.NET à l'aide des autorisations de sécurité  
 Dans les scénarios avec confiance partielle, vous pouvez exiger des privilèges de sécurité d'accès du code (CAS) pour des méthodes particulières dans votre code en spécifiant un objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Si ce privilège n'est pas autorisé par la stratégie de sécurité limitée en vigueur, une exception est levée avant que votre code soit exécuté. Pour plus d’informations sur la stratégie de sécurité, consultez [meilleures pratiques](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))pour la stratégie de sécurité et la [gestion des stratégies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) de sécurité.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment écrire un code requérant une chaîne de connexion particulière. Il simule le refus d'autorisations illimitées à <xref:System.Data.SqlClient>, qu'un administrateur système implémenterait à l'aide d'une stratégie de sécurité d'accès du code dans la réalité.  
  
> [!IMPORTANT]
> En cas d'utilisation d'autorisations de sécurité d'accès du code pour ADO.NET, le modèle correct consiste à commencer par le cas le plus restrictif (aucune autorisation) puis à ajouter les autorisations spécifiques nécessaires pour la tâche particulière que le code doit exécuter. En revanche, commencer par toutes les autorisations, puis tenter de refuser une autorisation spécifique n'est pas une approche sûre car il existe de nombreuses manières d'exprimer la même chaîne de connexion. Par exemple, si vous démarrez avec toutes les autorisations, puis refusez l'utilisation de la chaîne de connexion "server=someserver", vous pouvez continuer à utiliser "server=someserver.mycompany.com". En démarrant toujours en n'accordant aucune autorisation, vous limitez les risques de failles dans le jeu d'autorisations.  
  
 Le code suivant montre comment `SqlClient` exécute la demande de sécurité qui lève un objet <xref:System.Security.SecurityException> si les autorisations de sécurité d'accès du code (CAS) appropriées ne sont pas en place. Le résultat de l'objet <xref:System.Security.SecurityException> s'affiche dans la fenêtre de console.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Vous devez voir ce résultat dans la fenêtre Console :  
  
```output  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>Interopérabilité avec du code non managé  
 Le code qui s'exécute en dehors du CLR est appelé code non managé. Par conséquent, les mécanismes de sécurité, tels que la sécurité d'accès du code, ne peuvent pas être appliqués à du code non managé. Les composants COM, les interfaces ActiveX et les fonctions API Windows sont des exemples de code non managé. Des considérations de sécurité particulières s'appliquent lors de l'exécution de code non managé pour éviter de compromettre la sécurité globale des applications. Pour plus d’informations, consultez [Interopération avec du code non managé](../../interop/index.md).  
  
 Le .NET Framework prend également en charge la compatibilité descendante avec des composants COM existants en offrant un accès via COM Interop. Vous pouvez incorporer des composants COM dans une application .NET Framework en utilisant des outils de COM Interop pour importer les types COM pertinents. Une fois importés, les types COM sont prêts à être utilisés. COM Interop permet également aux clients COM d'accéder à du code managé en exportant des métadonnées d'assembly dans une bibliothèque de types et en inscrivant le composant managé en tant que composant COM. Pour plus d’informations, consultez [interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [Sécurité dans le code natif et .NET Framework](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Sécurité basée sur les rôles](../../../standard/security/role-based-security.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
