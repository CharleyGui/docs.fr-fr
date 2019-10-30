---
title: Utilisation de System.Transactions dans ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 2bddebc13897408839e18f42b17a9fbaefdc5b87
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040409"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="ebfaf-102">Utilisation de System.Transactions dans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebfaf-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="ebfaf-103">Cette rubrique explique comment utiliser <xref:System.Transactions> dans une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="ebfaf-104">Activation de DistributedTransactionPermission dans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebfaf-104">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="ebfaf-105"><xref:System.Transactions> prend en charge les appelants d'un niveau de confiance partiel et est marqué avec l'attribut `AllowPartiallyTrustedCallers` (APTCA).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-105"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="ebfaf-106">Les niveaux de confiance pour <xref:System.Transactions> sont définis en fonction des types de ressources (par exemple, la mémoire système, les ressources partagées au niveau du processus, les ressources système et d’autres ressources) que <xref:System.Transactions> expose et le niveau de confiance nécessaire pour y accéder. situées.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="ebfaf-107">Dans un environnement de confiance partielle, un assembly qui n’a pas un niveau de confiance totale ne peut utiliser que les transactions du domaine d’application (dans ce cas, les seules ressources protégées correspondent à la mémoire système), sauf s’il dispose de l’autorisation <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="ebfaf-108">L’autorisation<xref:System.Transactions.DistributedTransactionPermission> est demandée chaque fois que la gestion des transactions est remontée pour être managée par le MSDTC (Microsoft Distributed Transaction Coordinator).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="ebfaf-109">Ce genre de scénario utilise des ressources au niveau du processus et, en particulier, une ressource globale servant d’espace réservé dans le journal MSDTC.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="ebfaf-110">Par exemple, le composant web frontal d’une base de données ou une application qui utilise une base de donnée en tant que partie des services qu’il fournit.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="ebfaf-111">ASP.NET dispose de son propre jeu de niveaux de confiance et associe un jeu d'autorisations spécifique à ces niveaux de confiance via des fichiers de stratégie.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="ebfaf-112">Pour plus d’informations, consultez [ASP.net Trust levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="ebfaf-113">Lors de l’installation initiale de la SDK Windows, aucun des fichiers de stratégie ASP.NET par défaut n’est associé à la <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="ebfaf-114">Ainsi, lorsque votre transaction est remontée dans une application ASP.NET pour gestion par le MSDTC, la remontée échoue avec une <xref:System.Security.SecurityException> lors de la demande de <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="ebfaf-115">Pour activer la remontée des transactions au sein d'un environnement ASP.NET de confiance partielle, vous devez accorder l'autorisation <xref:System.Transactions.DistributedTransactionPermission> aux mêmes niveaux de confiance par défaut que ceux de l'autorisation <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="ebfaf-116">Vous pouvez configurer vos propres niveaux de confiance et fichier de stratégie personnalisés pour la prise en charge ou modifier les fichiers de stratégie par défaut : **Web_hightrust.config** et **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="ebfaf-117">Pour modifier les fichiers de stratégie, ajoutez un élément `SecurityClass` pour `DistributedTransactionPermission` à l'élément `SecurityClasses` sous l'élément `PolicyLevel` et ajoutez un élément `IPermission` correspondant sous le `NamedPermissionSet` ASP.NET pour System.Transactions.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-117">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="ebfaf-118">Le fichier de configuration suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-118">The following configuration file demonstrates this.</span></span>

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

 <span data-ttu-id="ebfaf-119">Pour plus d’informations sur la stratégie de sécurité ASP.NET, consultez [SecurityPolicy, élément (schéma des paramètres ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="ebfaf-120">Compilation dynamique</span><span class="sxs-lookup"><span data-stu-id="ebfaf-120">Dynamic Compilation</span></span>
 <span data-ttu-id="ebfaf-121">Pour importer et utiliser <xref:System.Transactions> dans une application ASP.NET compilée dynamiquement lors de l'accès, insérez une référence à l'assembly <xref:System.Transactions> dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="ebfaf-122">Plus précisément, la référence doit être ajoutée sous la section `compilation/assemblies` du fichier de configuration **Web. config** racine par défaut ou du fichier de configuration d’une application Web spécifique.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-122">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="ebfaf-123">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-123">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="ebfaf-124">Pour plus d’informations, consultez [Add, élément de Assemblies pour compilation (schéma des paramètres ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebfaf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebfaf-125">See also</span></span>

- <span data-ttu-id="ebfaf-126">[Niveaux de confiance ASP.NET et fichiers de stratégie](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ebfaf-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="ebfaf-127">[securityPolicy, élément (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ebfaf-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="ebfaf-128">Remontée de la gestion des transactions</span><span class="sxs-lookup"><span data-stu-id="ebfaf-128">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
