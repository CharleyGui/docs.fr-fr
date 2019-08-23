---
title: 'Procédure : Exécuter du code partiellement fiable dans un bac à sable (sandbox)'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a439e02046e04d8628415237d6717a74b9922371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910946"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="8b2f0-102">Procédure : Exécuter du code partiellement fiable dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="8b2f0-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8b2f0-103">L'utilisation de bac à sable (sandbox) consiste à exécuter du code dans un environnement de sécurité restreint qui limite les autorisations d'accès accordées au code.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="8b2f0-104">Par exemple, si une bibliothèque managée provient d'une source qui n'est pas totalement fiable, vous ne devez pas l'exécuter comme ayant un niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="8b2f0-105">Au lieu de cela, placez le code dans un bac à sable (sandbox) qui limite ses autorisations à ceux qui en ont besoin (par exemple, l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>).</span><span class="sxs-lookup"><span data-stu-id="8b2f0-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="8b2f0-106">Vous pouvez également utiliser un bac à sable (sandbox) pour tester le code pour tester du code à distribuer qui s'exécute dans des environnements partiellement fiables.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="8b2f0-107">Un <xref:System.AppDomain> est un moyen efficace de fournir un bac à sable (sandbox) pour les applications managées.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="8b2f0-108">Les domaines d'application utilisés pour l'exécution du code de niveau de confiance partiel disposent d'autorisations qui définissent les ressources protégées disponibles au moment de l'exécution dans ce <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="8b2f0-109">Le code qui s'exécute à l'intérieur du <xref:System.AppDomain> est lié au <xref:System.AppDomain> par les autorisations qui lui sont associées et est autorisé à accéder uniquement aux ressources spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="8b2f0-110">Le <xref:System.AppDomain> inclut également un tableau <xref:System.Security.Policy.StrongName> utilisé pour identifier les assemblys qui seront chargés avec un niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="8b2f0-111">Cela permet au concepteur d'un <xref:System.AppDomain> de démarrer un nouveau domaine bac à sable (sandbox) qui permet aux assemblys d'assistance spécifiques d'avoir un niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="8b2f0-112">Une autre option pour le chargement d'assemblys avec un niveau de confiance totale est de les placer dans le Global Assembly Cache ; toutefois, cela les charge avec un niveau de confiance totale dans tous les domaines d'application créés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="8b2f0-113">La liste des noms forts prend en charge une décision pour chaque <xref:System.AppDomain> qui fournit une détermination plus restrictive.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="8b2f0-114">Vous pouvez utiliser la surcharge de la méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pour définir le jeu d'autorisations des applications qui s'exécutent dans un bac à sable (sandbox).</span><span class="sxs-lookup"><span data-stu-id="8b2f0-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="8b2f0-115">Cette surcharge vous permet de spécifier le niveau de sécurité d'accès du code exact que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="8b2f0-116">Les assemblys chargés dans un <xref:System.AppDomain> à l'aide de cette surcharge peuvent disposer soit uniquement du jeu d'autorisations spécifié, soit de la confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="8b2f0-117">La confiance totale est accordée à l'assembly s'il se trouve dans le Global Assembly Cache ou est répertorié dans le paramètre de tableau `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>).</span><span class="sxs-lookup"><span data-stu-id="8b2f0-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="8b2f0-118">Seuls les assemblys réputés être entièrement fiables doivent être ajoutés à la liste `fullTrustAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="8b2f0-119">La surcharge possède la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="8b2f0-120">Les paramètres de la surcharge de méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> spécifient le nom du <xref:System.AppDomain>, la preuve du <xref:System.AppDomain>, l'objet <xref:System.AppDomainSetup> qui identifie la base de l'application pour le bac à sable (sandbox), le jeu d'autorisations à utiliser et les noms forts des assemblys entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="8b2f0-121">Pour des raisons de sécurité, la base de l'application définie dans le paramètre `info` ne doit pas être la base de l'application pour l'application d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="8b2f0-122">Pour le paramètre `grantSet`, vous pouvez spécifier un jeu d'autorisations que vous avez explicitement créé ou un jeu d'autorisations standard créé par la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="8b2f0-123">Contrairement à la plupart des surcharges <xref:System.AppDomain>, la preuve pour le <xref:System.AppDomain> (fournie par le paramètre `securityInfo`) n'est pas utilisée pour déterminer le jeu d'autorisations pour les assemblys partiellement fiables.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="8b2f0-124">Elle est en fait spécifiée indépendamment par le paramètre `grantSet`.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="8b2f0-125">Toutefois, la preuve peut être utilisée à d'autres fins, par exemple, pour déterminer la portée de stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="8b2f0-126">Pour exécuter une application dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="8b2f0-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="8b2f0-127">Créez le jeu d'autorisations à accorder à l'application non fiable.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="8b2f0-128">L'autorisation minimale que vous pouvez accorder est l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="8b2f0-129">Vous pouvez également accorder des autorisations supplémentaires que vous pensez sécurisées pour du code non fiable ; par exemple, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="8b2f0-130">Le code suivant crée un jeu d'autorisations uniquement avec l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="8b2f0-131">Vous pouvez également utiliser un jeu d'autorisations nommé existant, tel qu'Internet.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="8b2f0-132">En fonction de la zone dans la preuve, la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A> retourne un jeu d'autorisations `Internet` ou un jeu d'autorisations `LocalIntranet`.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="8b2f0-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> construit également des autorisations d'identité pour certains objets de preuve passés comme références.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="8b2f0-134">Signez l'assembly qui contient la classe d'hébergement (appelée `Sandboxer` dans cet exemple) qui appelle le code non fiable.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="8b2f0-135">Ajouter le <xref:System.Security.Policy.StrongName> utilisé pour signer l'assembly au tableau <xref:System.Security.Policy.StrongName> du paramètre `fullTrustAssemblies` paramètre de l'appel <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="8b2f0-136">La classe d'hébergement doit être exécutée avec un niveau de confiance totale pour permettre l'exécution du code de confiance partielle ou offrir des services à l'application de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="8b2f0-137">Voici comment lire le <xref:System.Security.Policy.StrongName> d'un assembly :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="8b2f0-138">Les assemblys .NET Framework tels que mscorlib et System.dll n'ont pas à être ajoutés à la liste de confiance totale, car ils sont chargés avec un niveau de confiance totale à partir du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="8b2f0-139">Initialisez le paramètre <xref:System.AppDomainSetup> de la méthode <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="8b2f0-140">Ce paramètre vous permet de contrôler la plupart des paramètres du nouveau <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="8b2f0-141">La propriété <xref:System.AppDomainSetup.ApplicationBase%2A> est un paramètre important qui doit être différent de la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> pour le <xref:System.AppDomain> de l'application d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="8b2f0-142">Si les paramètres <xref:System.AppDomainSetup.ApplicationBase%2A> sont les mêmes, l'application de confiance partielle peut amener l'application d'hébergement à charger (avec un niveau de confiance totale) une exception définie par ses soins, et donc l'exploiter.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="8b2f0-143">Cela fait partie des raisons pour lesquelles un Catch (exception) n'est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="8b2f0-144">En configurant la base d'application de l'hôte différemment de la base d'application de l'application bac à sable (sandbox), vous réduisez les risques d'attaques.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="8b2f0-145">Appelez la surcharge de méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> pour créer le domaine d'application à l'aide des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="8b2f0-146">La signature de cette méthode est :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="8b2f0-147">Informations complémentaires :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-147">Additional information:</span></span>  
  
    - <span data-ttu-id="8b2f0-148">Il s'agit de la seule surcharge de la méthode <xref:System.AppDomain.CreateDomain%2A> prenant un <xref:System.Security.PermissionSet> comme paramètre, et donc la seule surcharge qui vous permet de charger une application dans un paramètre de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="8b2f0-149">Le paramètre `evidence` n'est pas utilisé pour calculer un jeu d'autorisations, mais pour être identifié par les autres fonctionnalités du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="8b2f0-150">La définition de la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> du paramètre `info` est obligatoire pour cette surcharge.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="8b2f0-151">Le paramètre `fullTrustAssemblies` possède le mot clé `params`, ce qui signifie qu'il n'est pas nécessaire de créer un tableau <xref:System.Security.Policy.StrongName>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="8b2f0-152">Passer 0, 1 ou plusieurs noms forts comme paramètres est autorisé.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="8b2f0-153">Le code servant à créer le domaine d'application est le suivant :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="8b2f0-154">Chargez le code dans le <xref:System.AppDomain> bac à sable (sandbox) que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="8b2f0-155">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="8b2f0-156">Appelez la méthode <xref:System.AppDomain.ExecuteAssembly%2A> pour l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="8b2f0-157">Utilisez la méthode <xref:System.Activator.CreateInstanceFrom%2A> pour créer une instance d'une classe dérivée de <xref:System.MarshalByRefObject> dans le nouveau <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="8b2f0-158">La seconde méthode est préférable, car elle simplifie le passage des paramètres à la nouvelle instance <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="8b2f0-159">La méthode <xref:System.Activator.CreateInstanceFrom%2A> fournit deux fonctionnalités importantes :</span><span class="sxs-lookup"><span data-stu-id="8b2f0-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="8b2f0-160">Vous pouvez utiliser une base de code qui pointe vers un emplacement qui ne contient pas votre assembly.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="8b2f0-161">Vous pouvez effectuer la création sous un <xref:System.Security.CodeAccessPermission.Assert%2A> pour la confiance totale (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), ce qui vous permet de créer une instance d'une classe critique.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="8b2f0-162">(Cela se produit chaque fois que votre assembly n'a pas de marquages de transparence et est chargé avec un niveau de confiance totale.) Vous devez donc vous assurer de ne créer que du code fiable avec cette fonction. Nous vous recommandons de créer uniquement des instances de classes d'un niveau de confiance totale dans le nouveau domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="8b2f0-163">Notez que pour créer une instance d'une classe dans un nouveau domaine, cette classe doit étendre la classe <xref:System.MarshalByRefObject>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="8b2f0-164">Désencapsulez la nouvelle instance de domaine dans une référence de ce domaine.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="8b2f0-165">Cette référence est utilisée pour exécuter le code non fiable.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="8b2f0-166">Appelez la méthode `ExecuteUntrustedCode` dans l'instance de la classe `Sandboxer` que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="8b2f0-167">Cet appel est exécuté dans le domaine d'application bac à sable (sandbox), qui possède des autorisations restreintes.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="8b2f0-168"><xref:System.Reflection> est utilisé pour obtenir le handle d'une méthode dans l'assembly de niveau de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="8b2f0-169">Le handle permet d'exécuter du code d'une façon sécurisée avec les autorisations minimales.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="8b2f0-170">Dans le code précédent, notez <xref:System.Security.PermissionSet.Assert%2A> pour l'autorisation de confiance totale avant l'affichage de <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="8b2f0-171">L'assertion de confiance totale permet d'obtenir les informations détaillées de <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="8b2f0-172">Sans <xref:System.Security.PermissionSet.Assert%2A>, la méthode <xref:System.Security.SecurityException.ToString%2A> de <xref:System.Security.SecurityException> détecte que du code de niveau de confiance partielle se trouve sur la pile et restreint les informations retournées.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="8b2f0-173">Cela peut provoquer des problèmes de sécurité si le code de confiance partielle peut lire ces informations. Cependant, le risque est atténué par le fait de ne pas accorder <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="8b2f0-174">L'assertion de confiance totale doit être utilisée avec modération et uniquement quand vous êtes sûr de ne pas autoriser du code à passer du niveau de confiance partielle au niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="8b2f0-175">En règle générale, n'appelez pas de code non fiable dans la même fonction et après avoir appelé une assertion de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="8b2f0-176">Nous vous conseillons de toujours rétablir l'assertion quand vous avez terminé de l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b2f0-177">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b2f0-177">Example</span></span>  
 <span data-ttu-id="8b2f0-178">L'exemple suivant implémente la procédure de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="8b2f0-179">Dans l'exemple, un projet nommé `Sandboxer` dans une solution Visual Studio contient également un projet nommé `UntrustedCode`, qui implémente la classe `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="8b2f0-180">Ce scénario suppose que vous avez téléchargé un assembly de bibliothèque qui contient une méthode censée retourner la valeur `true` ou `false` pour indiquer si le nombre que vous avez fourni est un nombre de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="8b2f0-181">À la place, la méthode essaie de lire un fichier de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="8b2f0-182">L'exemple suivant illustre le code non fiable.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8b2f0-183">L'exemple suivant montre le code de l'application `Sandboxer` qui exécute le code non fiable.</span><span class="sxs-lookup"><span data-stu-id="8b2f0-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b2f0-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b2f0-184">See also</span></span>

- [<span data-ttu-id="8b2f0-185">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="8b2f0-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
