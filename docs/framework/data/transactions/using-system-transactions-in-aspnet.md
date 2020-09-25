---
title: Utilisation de System.Transactions dans ASP.NET
description: Utilisez System. transactions à l’intérieur d’une application ASP.NET. Activez les autorisations de transaction distribuée et utilisez la compilation dynamique.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: b6663e9258e98e94d7b739ee75c826ced1e2f897
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186716"
---
# <a name="using-systemtransactions-in-aspnet"></a>Utilisation de System.Transactions dans ASP.NET

Cette rubrique explique comment utiliser <xref:System.Transactions> dans une application ASP.NET.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Activation de DistributedTransactionPermission dans ASP.NET

 <xref:System.Transactions> prend en charge les appelants d’un niveau de confiance partiel et est marqué avec l' `AllowPartiallyTrustedCallers` attribut (APTCA). Les niveaux de confiance pour <xref:System.Transactions> sont définis en fonction des types de ressources (par exemple, la mémoire système, les ressources partagées au niveau du processus, les ressources système et d’autres ressources) qui <xref:System.Transactions> exposent et le niveau de confiance requis pour accéder à ces ressources. Dans un environnement de confiance partielle, un assembly qui n’a pas un niveau de confiance totale ne peut utiliser que les transactions du domaine d’application (dans ce cas, les seules ressources protégées correspondent à la mémoire système), sauf s’il dispose de l’autorisation <xref:System.Transactions.DistributedTransactionPermission>.

 L’autorisation<xref:System.Transactions.DistributedTransactionPermission> est demandée chaque fois que la gestion des transactions est remontée pour être managée par le MSDTC (Microsoft Distributed Transaction Coordinator). Ce genre de scénario utilise des ressources au niveau du processus et, en particulier, une ressource globale servant d’espace réservé dans le journal MSDTC. Par exemple, le composant web frontal d’une base de données ou une application qui utilise une base de donnée en tant que partie des services qu’il fournit.

 ASP.NET dispose de son propre jeu de niveaux de confiance et associe un jeu d'autorisations spécifique à ces niveaux de confiance via des fichiers de stratégie. Pour plus d’informations, consultez [ASP.net Trust levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)). Lors de l’installation initiale de la SDK Windows, aucun des fichiers de stratégie ASP.NET par défaut n’est associé au <xref:System.Transactions.DistributedTransactionPermission> . Ainsi, lorsque votre transaction est remontée dans une application ASP.NET pour gestion par le MSDTC, la remontée échoue avec une <xref:System.Security.SecurityException> lors de la demande de <xref:System.Transactions.DistributedTransactionPermission>. Pour activer la remontée des transactions au sein d'un environnement ASP.NET de confiance partielle, vous devez accorder l'autorisation <xref:System.Transactions.DistributedTransactionPermission> aux mêmes niveaux de confiance par défaut que ceux de l'autorisation <xref:System.Data.SqlClient.SqlClientPermission>. Vous pouvez configurer vos propres niveaux de confiance et fichier de stratégie personnalisés pour la prise en charge ou modifier les fichiers de stratégie par défaut : **Web_hightrust.config** et **Web_mediumtrust.config**.

 Pour modifier les fichiers de stratégie, ajoutez un `SecurityClass` élément pour `DistributedTransactionPermission` à l' `SecurityClasses` élément sous l' `PolicyLevel` élément et ajoutez un `IPermission` élément correspondant sous le ASP.NET `NamedPermissionSet` pour System. transactions. Le fichier de configuration suivant illustre ceci.

```xml
<SecurityClasses>
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
...
</SecurityClasses>

<PermissionSet
  class="NamedPermissionSet"
  version="1"
  Name="ASP.Net">
     <IPermission
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
        version="1"
        Unrestricted="true"
     />
...
</PermissionSet>
```

 Pour plus d’informations sur la stratégie de sécurité ASP.NET, consultez [SecurityPolicy, élément (schéma des paramètres ASP.net)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).

## <a name="dynamic-compilation"></a>Compilation dynamique

 Pour importer et utiliser <xref:System.Transactions> dans une application ASP.NET compilée dynamiquement lors de l'accès, insérez une référence à l'assembly <xref:System.Transactions> dans le fichier de configuration. Plus précisément, la référence doit être ajoutée sous la `compilation/assemblies` section du fichier de configuration **Web.config** racine par défaut ou du fichier de configuration d’une application Web spécifique. l’exemple ci-dessous illustre ce cas de figure.

```xml
<configuration>
   <system.web>
      <compilation>
         <assemblies>
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         </assemblies>
      </compilation>
   </system.web>
</configuration>
```

 Pour plus d’informations, consultez [Add, élément de Assemblies pour compilation (schéma des paramètres ASP.net)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).

## <a name="see-also"></a>Voir aussi

- [Niveaux de confiance ASP.NET et fichiers de stratégie](/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy élément (Schéma des paramètres ASP.NET)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Remontée de la gestion des transactions](transaction-management-escalation.md)
