---
title: Authentification dans SQL Server
description: En savoir plus sur l’authentification avec SQL Server pour ADO.NET, notamment le mode d’authentification Windows et le mode mixte.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 2c4f62391a0d9b5ada27f56eef4c3467d99b4c6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197527"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="e223c-103">Authentification dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="e223c-103">Authentication in SQL Server</span></span>

<span data-ttu-id="e223c-104">SQL Server prend en charge deux modes d’authentification : le mode d’authentification Windows et le mode mixte.</span><span class="sxs-lookup"><span data-stu-id="e223c-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="e223c-105">L’authentification Windows correspond au mode par défaut, et il est souvent qualifié de sécurité intégrée car ce modèle de sécurité SQL Server est étroitement intégré à Windows.</span><span class="sxs-lookup"><span data-stu-id="e223c-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="e223c-106">Des comptes d’utilisateur et groupes Windows spécifiques sont approuvés pour se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="e223c-107">Les utilisateurs Windows qui ont déjà été authentifiés n’ont pas besoin de présenter des informations d’identification supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e223c-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="e223c-108">Le mode mixte prend en charge l’authentification par Windows et par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="e223c-109">Les paires nom d’utilisateur–mot de passe sont conservées dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e223c-110">Nous vous recommandons d’utiliser l’authentification Windows dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="e223c-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="e223c-111">L’authentification Windows utilise une série de messages chiffrés pour authentifier les utilisateurs dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="e223c-112">Quand des connexions SQL Server sont utilisées, les noms de connexion SQL Server et les mots de passe chiffrés sont transmis sur le réseau, ce qui les rend moins sûrs.</span><span class="sxs-lookup"><span data-stu-id="e223c-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="e223c-113">Avec l’authentification Windows, les utilisateurs ont déjà ouvert une session Windows et n’ont pas besoin d’ouvrir une session SQL Server distincte.</span><span class="sxs-lookup"><span data-stu-id="e223c-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="e223c-114">Le `SqlConnection.ConnectionString` suivant spécifie l’authentification Windows sans que les utilisateurs aient besoin de spécifier un nom d’utilisateur ou un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e223c-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="e223c-115">Les connexions sont différentes des utilisateurs de base de données.</span><span class="sxs-lookup"><span data-stu-id="e223c-115">Logins are distinct from database users.</span></span> <span data-ttu-id="e223c-116">Vous devez mapper des connexions ou des groupes Windows à des utilisateurs ou des rôles de base de données dans une opération distincte.</span><span class="sxs-lookup"><span data-stu-id="e223c-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="e223c-117">Vous accordez ensuite des autorisations aux utilisateurs ou aux rôles pour accéder aux objets de base de données.</span><span class="sxs-lookup"><span data-stu-id="e223c-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="e223c-118">Scénarios d'authentification</span><span class="sxs-lookup"><span data-stu-id="e223c-118">Authentication Scenarios</span></span>  

 <span data-ttu-id="e223c-119">L’authentification Windows est généralement le meilleur choix dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e223c-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="e223c-120">Il y a un contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="e223c-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="e223c-121">L’application et la base de données se trouvent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e223c-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="e223c-122">Vous utilisez une instance de SQL Server Express ou LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e223c-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="e223c-123">Les connexions SQL Server sont souvent utilisées dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e223c-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="e223c-124">Si vous avez un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="e223c-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="e223c-125">Les utilisateurs se connectent à partir de domaines différents et non approuvés.</span><span class="sxs-lookup"><span data-stu-id="e223c-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="e223c-126">Applications Internet, comme ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e223c-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e223c-127">La spécification de l’authentification Windows ne désactive pas les connexions SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="e223c-128">Utilisez l’instruction Transact-SQL ALTER LOGIN DISABLE pour désactiver des connexions SQL Server dotées de privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="e223c-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="e223c-129">Types de connexions</span><span class="sxs-lookup"><span data-stu-id="e223c-129">Login Types</span></span>  

 <span data-ttu-id="e223c-130">SQL Server prend en charge trois types de connexions :</span><span class="sxs-lookup"><span data-stu-id="e223c-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="e223c-131">Un compte d’utilisateur Windows local ou un compte de domaine approuvé.</span><span class="sxs-lookup"><span data-stu-id="e223c-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="e223c-132">SQL Server s’appuie sur Windows pour authentifier les comptes d’utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="e223c-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="e223c-133">Groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="e223c-133">Windows group.</span></span> <span data-ttu-id="e223c-134">L’octroi de l’accès à un groupe Windows accorde l’accès à toutes les connexions utilisateur Windows qui sont membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="e223c-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="e223c-135">Connexion SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-135">SQL Server login.</span></span> <span data-ttu-id="e223c-136">SQL Server stocke le nom d’utilisateur et un hachage du mot de passe dans la base de données MASTER, en utilisant des méthodes d’authentification internes pour vérifier les tentatives de connexion.</span><span class="sxs-lookup"><span data-stu-id="e223c-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e223c-137">SQL Server fournit des connexions créées à partir de certificats ou de clés asymétriques qui sont utilisées seulement pour la signature de code.</span><span class="sxs-lookup"><span data-stu-id="e223c-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="e223c-138">Elles ne peuvent pas être utilisées pour se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="e223c-139">Authentification en mode mixte</span><span class="sxs-lookup"><span data-stu-id="e223c-139">Mixed Mode Authentication</span></span>  

 <span data-ttu-id="e223c-140">Si vous devez utiliser l’authentification en mode mixte, vous devez créer des connexions SQL Server, qui sont stockées dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="e223c-141">Vous devez ensuite fournir le nom d’utilisateur et le mot de passe SQL Server au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e223c-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e223c-142">SQL Server est installé avec une connexion SQL Server nommée `sa` (abréviation d’« administrateur système »).</span><span class="sxs-lookup"><span data-stu-id="e223c-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="e223c-143">Attribuez un mot de passe fort à la connexion `sa` et n’utilisez pas la connexion `sa` dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e223c-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="e223c-144">La connexion `sa` est mappée au rôle serveur fixe `sysadmin`, qui a des informations d’identification d’administration irrévocables sur l’ensemble du serveur.</span><span class="sxs-lookup"><span data-stu-id="e223c-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="e223c-145">Il n’existe aucune limite aux dommages potentiels si une personne malveillante obtient l’accès en tant qu’administrateur système.</span><span class="sxs-lookup"><span data-stu-id="e223c-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="e223c-146">Tous les membres du groupe `BUILTIN\Administrators` Windows (groupe des administrateurs locaux) sont membres du rôle `sysadmin` par défaut, mais peuvent être supprimés de ce rôle.</span><span class="sxs-lookup"><span data-stu-id="e223c-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="e223c-147">SQL Server fournit des mécanismes de stratégie de mot de passe Windows pour les connexions SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="e223c-148">Les stratégies de mot de passe complexes sont conçues pour décourager les attaques en augmentant le nombre de mots de passe possibles.</span><span class="sxs-lookup"><span data-stu-id="e223c-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="e223c-149">SQL Server pouvez appliquer les mêmes stratégies de complexité et d’expiration aux mots de passe utilisés dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e223c-150">La concaténation de chaînes de connexion à partir d’entrées utilisateur peut vous rendre vulnérable à une attaque par injection de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="e223c-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="e223c-151">Utilisez le <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion syntaxiquement valides au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e223c-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="e223c-152">Pour plus d’informations, consultez [Builders de chaînes de connexion](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="e223c-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e223c-153">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="e223c-153">External Resources</span></span>  

 <span data-ttu-id="e223c-154">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e223c-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="e223c-155">Ressource</span><span class="sxs-lookup"><span data-stu-id="e223c-155">Resource</span></span>|<span data-ttu-id="e223c-156">Description</span><span class="sxs-lookup"><span data-stu-id="e223c-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="e223c-157">Principaux</span><span class="sxs-lookup"><span data-stu-id="e223c-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="e223c-158">Décrit les connexions et autres principaux de sécurité dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e223c-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e223c-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e223c-159">See also</span></span>

- [<span data-ttu-id="e223c-160">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e223c-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="e223c-161">Scénarios de sécurité des applications dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="e223c-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="e223c-162">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="e223c-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="e223c-163">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="e223c-163">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="e223c-164">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e223c-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
