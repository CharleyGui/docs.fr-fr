---
title: 'Comment : désactiver la fonctionnalité de contournement de nom fort'
description: Le contournement de nom fort ignore la validation de signature dans les domaines de confiance totale dans .NET. Vous pouvez remplacer cette fonctionnalité pour une application unique ou toutes les applications.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 2846efbbd76cf677a42a7031e53661d302c6c964
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687461"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="cddad-104">Comment : désactiver la fonctionnalité de contournement de nom fort</span><span class="sxs-lookup"><span data-stu-id="cddad-104">How to: Disable the strong-name bypass feature</span></span>

<span data-ttu-id="cddad-105">À partir du .NET Framework version 3.5 Service Pack 1 (SP1), les signatures de noms forts ne sont pas validées quand un assembly est chargé dans un objet <xref:System.AppDomain> de confiance totale, tel que le <xref:System.AppDomain> par défaut pour la zone `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="cddad-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="cddad-106">Cette fonctionnalité permet d’ignorer les noms forts.</span><span class="sxs-lookup"><span data-stu-id="cddad-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="cddad-107">Dans un environnement de confiance totale, les demandes de <xref:System.Security.Permissions.StrongNameIdentityPermission> aboutissent toujours pour les assemblys de confiance totale signés, quelle que soit leur signature.</span><span class="sxs-lookup"><span data-stu-id="cddad-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="cddad-108">La seule restriction est que l’assembly doit être entièrement fiable, car sa zone est entièrement fiable.</span><span class="sxs-lookup"><span data-stu-id="cddad-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="cddad-109">Le nom fort n’étant pas un facteur déterminant dans ces conditions, il n’y a aucune raison pour qu’il soit validé.</span><span class="sxs-lookup"><span data-stu-id="cddad-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="cddad-110">Ignorer la validation des signatures de noms forts fournit une amélioration significative des performances.</span><span class="sxs-lookup"><span data-stu-id="cddad-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="cddad-111">Cette fonctionnalité consistant à ignorer la validation s’applique à tout assembly de confiance totale qui n’est pas à signature différée et qui est chargé dans n’importe quel <xref:System.AppDomain> de confiance totale à partir du répertoire spécifié par sa propriété <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="cddad-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="cddad-112">Vous pouvez outrepasser cette fonctionnalité pour toutes les applications sur un ordinateur en définissant une valeur de clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="cddad-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="cddad-113">Vous pouvez remplacer le paramètre pour une application unique en utilisant un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cddad-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="cddad-114">Vous ne pouvez pas rétablir cette fonctionnalité pour une application si elle a été désactivée par la clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="cddad-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="cddad-115">Quand vous outrepassez cette fonctionnalité, seule l’exactitude du nom fort est validée ; aucune vérification n’est effectuée pour <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="cddad-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="cddad-116">Si vous souhaitez confirmer un nom fort spécifique, vous devez effectuer un contrôle distinct.</span><span class="sxs-lookup"><span data-stu-id="cddad-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cddad-117">La possibilité de forcer la validation des noms forts dépend d’une clé de Registre, comme décrit dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="cddad-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="cddad-118">Si une application s’exécute sous un compte qui ne dispose pas de l’autorisation ACL (liste de contrôle d’accès) d’accès à cette clé de Registre, le paramètre est inefficace.</span><span class="sxs-lookup"><span data-stu-id="cddad-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="cddad-119">Vous devez vérifier que les droits ACL sont configurés pour cette clé afin qu’elle puisse être lue pour tous les assemblys.</span><span class="sxs-lookup"><span data-stu-id="cddad-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="cddad-120">Désactiver la fonctionnalité de contournement de nom fort pour toutes les applications</span><span class="sxs-lookup"><span data-stu-id="cddad-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="cddad-121">Sur les ordinateurs 32 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="cddad-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="cddad-122">Sur les ordinateurs 64 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous les clés HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework et HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="cddad-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="cddad-123">Désactiver la fonctionnalité de contournement de nom fort pour une seule application</span><span class="sxs-lookup"><span data-stu-id="cddad-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="cddad-124">Ouvrez ou créez le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="cddad-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="cddad-125">Pour plus d’informations sur ce fichier, consultez la section fichiers de configuration de l’application dans [configurer des applications](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="cddad-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="cddad-126">Ajoutez l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="cddad-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="cddad-127">Vous pouvez restaurer la fonctionnalité de contournement pour l’application en supprimant le paramètre du fichier de configuration ou en affectant à l’attribut la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="cddad-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cddad-128">Vous pouvez activer et désactiver la validation des noms forts pour une application uniquement si la fonctionnalité consistant à ignorer la validation est activée pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cddad-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="cddad-129">Si cette fonctionnalité a été désactivée pour l’ordinateur, les noms forts sont validés pour toutes les applications et vous ne pouvez pas ignorer la validation pour une application unique.</span><span class="sxs-lookup"><span data-stu-id="cddad-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddad-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cddad-130">See also</span></span>

- [<span data-ttu-id="cddad-131">Sn.exe (outil Strong Name Tool)</span><span class="sxs-lookup"><span data-stu-id="cddad-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="cddad-132">\<bypassTrustedAppStrongNames> appartient</span><span class="sxs-lookup"><span data-stu-id="cddad-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="cddad-133">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="cddad-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
