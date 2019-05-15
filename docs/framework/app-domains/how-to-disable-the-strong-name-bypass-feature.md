---
title: 'Procédure : désactiver la fonctionnalité consistant à ignorer les noms forts'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20b482ee94446ffa863697d8c25276658a4bb122
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593612"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="5a057-102">Procédure : désactiver la fonctionnalité consistant à ignorer les noms forts</span><span class="sxs-lookup"><span data-stu-id="5a057-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="5a057-103">À partir du .NET Framework version 3.5 Service Pack 1 (SP1), les signatures de noms forts ne sont pas validées quand un assembly est chargé dans un objet <xref:System.AppDomain> de confiance totale, tel que le <xref:System.AppDomain> par défaut pour la zone `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="5a057-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="5a057-104">Cette fonctionnalité permet d’ignorer les noms forts.</span><span class="sxs-lookup"><span data-stu-id="5a057-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="5a057-105">Dans un environnement de confiance totale, les demandes de <xref:System.Security.Permissions.StrongNameIdentityPermission> aboutissent toujours pour les assemblys de confiance totale signés, quelle que soit leur signature.</span><span class="sxs-lookup"><span data-stu-id="5a057-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="5a057-106">La seule restriction est que l’assembly doit être entièrement fiable, car sa zone est entièrement fiable.</span><span class="sxs-lookup"><span data-stu-id="5a057-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="5a057-107">Le nom fort n’étant pas un facteur déterminant dans ces conditions, il n’y a aucune raison pour qu’il soit validé.</span><span class="sxs-lookup"><span data-stu-id="5a057-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="5a057-108">Ignorer la validation des signatures de noms forts fournit une amélioration significative des performances.</span><span class="sxs-lookup"><span data-stu-id="5a057-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="5a057-109">Cette fonctionnalité consistant à ignorer la validation s’applique à tout assembly de confiance totale qui n’est pas à signature différée et qui est chargé dans n’importe quel <xref:System.AppDomain> de confiance totale à partir du répertoire spécifié par sa propriété <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a057-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="5a057-110">Vous pouvez outrepasser cette fonctionnalité pour toutes les applications sur un ordinateur en définissant une valeur de clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="5a057-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="5a057-111">Vous pouvez remplacer le paramètre pour une application unique en utilisant un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5a057-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="5a057-112">Vous ne pouvez pas rétablir cette fonctionnalité pour une application si elle a été désactivée par la clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="5a057-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="5a057-113">Quand vous outrepassez cette fonctionnalité, seule l’exactitude du nom fort est validée ; aucune vérification n’est effectuée pour <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="5a057-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="5a057-114">Si vous souhaitez confirmer un nom fort spécifique, vous devez effectuer un contrôle distinct.</span><span class="sxs-lookup"><span data-stu-id="5a057-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a057-115">La possibilité de forcer la validation des noms forts dépend d’une clé de Registre, comme décrit dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="5a057-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="5a057-116">Si une application s’exécute sous un compte qui ne dispose pas de l’autorisation ACL (liste de contrôle d’accès) d’accès à cette clé de Registre, le paramètre est inefficace.</span><span class="sxs-lookup"><span data-stu-id="5a057-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="5a057-117">Vous devez vérifier que les droits ACL sont configurés pour cette clé afin qu’elle puisse être lue pour tous les assemblys.</span><span class="sxs-lookup"><span data-stu-id="5a057-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="5a057-118">Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour toutes les applications</span><span class="sxs-lookup"><span data-stu-id="5a057-118">To disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="5a057-119">Sur les ordinateurs 32 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="5a057-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="5a057-120">Sur les ordinateurs 64 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous les clés HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework et HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="5a057-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="5a057-121">Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour une seule application</span><span class="sxs-lookup"><span data-stu-id="5a057-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="5a057-122">Ouvrez ou créez le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5a057-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="5a057-123">Pour plus d’informations sur ce fichier, consultez la section Fichiers de configuration de l’application dans [Configuration des applications](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a057-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="5a057-124">Ajoutez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="5a057-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="5a057-125">Vous pouvez restaurer la fonctionnalité pour l’application en supprimant le paramètre du fichier de configuration ou en affectant la valeur « true » à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="5a057-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a057-126">Vous pouvez activer et désactiver la validation des noms forts pour une application uniquement si la fonctionnalité consistant à ignorer la validation est activée pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a057-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="5a057-127">Si cette fonctionnalité a été désactivée pour l’ordinateur, les noms forts sont validés pour toutes les applications et vous ne pouvez pas ignorer la validation pour une application unique.</span><span class="sxs-lookup"><span data-stu-id="5a057-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a057-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a057-128">See also</span></span>

- [<span data-ttu-id="5a057-129">Sn.exe (outil Strong Name)</span><span class="sxs-lookup"><span data-stu-id="5a057-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="5a057-130">\<bypassTrustedAppStrongNames>, élément</span><span class="sxs-lookup"><span data-stu-id="5a057-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="5a057-131">Création et utilisation d’assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="5a057-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
