---
title: Compatibilité de la stratégie de sécurité d'accès du code et migration
description: Lisez un résumé et consultez des liens sur la compatibilité et la migration des stratégies de sécurité d’accès du code dans .NET Framework 4.
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 389976556175c0b6b300e75d01327d91f94f0db9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733384"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="ae10f-103">Compatibilité de la stratégie de sécurité d'accès du code et migration</span><span class="sxs-lookup"><span data-stu-id="ae10f-103">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="ae10f-104">La partie stratégie de la sécurité d’accès du code (CAS) a été rendue obsolète dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ae10f-104">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="ae10f-105">Par conséquent, vous pouvez rencontrer des avertissements de compilation et des exceptions d’exécution si vous appelez les membres et les types de stratégie obsolètes [explicitement](#explicit_use) ou [implicitement](#implicit_use) (par le biais d’autres types et membres).</span><span class="sxs-lookup"><span data-stu-id="ae10f-105">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="ae10f-106">Vous pouvez éviter les avertissements et les erreurs comme suit :</span><span class="sxs-lookup"><span data-stu-id="ae10f-106">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="ae10f-107">[Migration](#migration) vers le .NET Framework 4 remplacements pour les appels obsolètes.</span><span class="sxs-lookup"><span data-stu-id="ae10f-107">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="ae10f-108">\- ou -</span><span class="sxs-lookup"><span data-stu-id="ae10f-108">\- or -</span></span>

- <span data-ttu-id="ae10f-109">Utilisation de l' [ \<NetFx40_LegacySecurityPolicy> élément de configuration](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pour choisir le comportement de stratégie CAS hérité.</span><span class="sxs-lookup"><span data-stu-id="ae10f-109">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="ae10f-110">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae10f-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="ae10f-111">Utilisation explicite</span><span class="sxs-lookup"><span data-stu-id="ae10f-111">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="ae10f-112">Utilisation implicite</span><span class="sxs-lookup"><span data-stu-id="ae10f-112">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="ae10f-113">Erreurs et avertissements</span><span class="sxs-lookup"><span data-stu-id="ae10f-113">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="ae10f-114">Migration : remplacement des appels obsolètes</span><span class="sxs-lookup"><span data-stu-id="ae10f-114">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="ae10f-115">Compatibilité : utilisation de l'option de stratégie CAS héritée</span><span class="sxs-lookup"><span data-stu-id="ae10f-115">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="ae10f-116">Utilisation explicite</span><span class="sxs-lookup"><span data-stu-id="ae10f-116">Explicit Use</span></span>

<span data-ttu-id="ae10f-117">Les membres qui manipulent directement la stratégie de sécurité ou nécessitent la stratégie CAS en mode bac à sable (sandbox) sont obsolètes et généreront des erreurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae10f-117">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="ae10f-118">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="ae10f-118">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="ae10f-119">Utilisation implicite</span><span class="sxs-lookup"><span data-stu-id="ae10f-119">Implicit Use</span></span>

<span data-ttu-id="ae10f-120">Plusieurs surcharges de chargement d'assembly génèrent des erreurs du fait de leur utilisation implicite de stratégie CAS.</span><span class="sxs-lookup"><span data-stu-id="ae10f-120">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="ae10f-121">Ces surcharges prennent un paramètre <xref:System.Security.Policy.Evidence> utilisé pour résoudre la stratégie CAS et fournissent un jeu d'autorisations pour un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae10f-121">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="ae10f-122">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="ae10f-122">Here are some examples.</span></span> <span data-ttu-id="ae10f-123">Les surcharges obsolètes sont celles qui prennent <xref:System.Security.Policy.Evidence> comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="ae10f-123">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="ae10f-124">Erreurs et avertissements</span><span class="sxs-lookup"><span data-stu-id="ae10f-124">Errors and Warnings</span></span>

<span data-ttu-id="ae10f-125">Les types et membres obsolètes produisent les messages d'erreur suivants quand ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="ae10f-125">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="ae10f-126">Notez que le type <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> lui-même n'est pas obsolète.</span><span class="sxs-lookup"><span data-stu-id="ae10f-126">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="ae10f-127">Avertissement au moment de la compilation : </span><span class="sxs-lookup"><span data-stu-id="ae10f-127">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="ae10f-128">Exceptions runtime :</span><span class="sxs-lookup"><span data-stu-id="ae10f-128">Run-time exception:</span></span>

<span data-ttu-id="ae10f-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="ae10f-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="ae10f-130">Migration : remplacement des appels obsolètes</span><span class="sxs-lookup"><span data-stu-id="ae10f-130">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="ae10f-131">Détermination du niveau de confiance d'un assembly</span><span class="sxs-lookup"><span data-stu-id="ae10f-131">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="ae10f-132">La stratégie CAS est souvent utilisée pour déterminer le jeu d'autorisations ou le niveau de confiance d'un assembly ou d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="ae10f-132">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="ae10f-133">Le .NET Framework 4 expose les propriétés utiles suivantes qui n’ont pas besoin de résoudre la stratégie de sécurité :</span><span class="sxs-lookup"><span data-stu-id="ae10f-133">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="ae10f-134">Utilisation de bac à sable (sandbox) pour les domaines d'application</span><span class="sxs-lookup"><span data-stu-id="ae10f-134">Application Domain Sandboxing</span></span>

<span data-ttu-id="ae10f-135">La méthode <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> est généralement utilisée pour la mise en bac à sable (sandbox) des assemblys dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="ae10f-135">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="ae10f-136">Le .NET Framework 4 expose les membres qui n’ont pas à être utilisés à <xref:System.Security.Policy.PolicyLevel> cette fin.</span><span class="sxs-lookup"><span data-stu-id="ae10f-136">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="ae10f-137">Pour plus d’informations, consultez [Comment : exécuter du code d’un degré de confiance partiel dans un bac à sable (sandbox)](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="ae10f-137">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="ae10f-138">Détermination d'un jeu d'autorisations sécurisé ou raisonnable pour le code d'un niveau de confiance partiel</span><span class="sxs-lookup"><span data-stu-id="ae10f-138">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="ae10f-139">Les hôtes doivent souvent déterminer les autorisations qui sont appropriées pour l'utilisation de bacs à sable (sandbox) pour le code hébergé.</span><span class="sxs-lookup"><span data-stu-id="ae10f-139">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="ae10f-140">Avant la .NET Framework 4, la stratégie CAS fournissait une manière de le faire avec la <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="ae10f-140">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae10f-141">En remplacement, .NET Framework 4 fournit la <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> méthode, qui retourne un jeu d’autorisations standard sécurisé pour la preuve fournie.</span><span class="sxs-lookup"><span data-stu-id="ae10f-141">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="ae10f-142">Scénarios autres que le mode bac à sable (sandbox) : surcharges pour les chargements d'assemblys</span><span class="sxs-lookup"><span data-stu-id="ae10f-142">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="ae10f-143">La raison de l'utilisation d'une surcharge de chargement d'assembly peut être de recourir à des paramètres qui ne sont pas autrement disponibles, au lieu d'utiliser le sandbox pour l'assembly.</span><span class="sxs-lookup"><span data-stu-id="ae10f-143">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="ae10f-144">À partir du .NET Framework 4, les surcharges de chargement d’assembly qui ne nécessitent pas d' <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objet en tant que paramètre, par exemple, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> permettent ce scénario.</span><span class="sxs-lookup"><span data-stu-id="ae10f-144">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="ae10f-145">Si vous voulez utiliser un bac à sable (sandbox) pour un assembly, utilisez la surcharge <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae10f-145">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="ae10f-146">Compatibilité : utilisation de l'option de stratégie CAS héritée</span><span class="sxs-lookup"><span data-stu-id="ae10f-146">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="ae10f-147">L' [ \<NetFx40_LegacySecurityPolicy> élément de configuration](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) vous permet de spécifier qu’un processus ou une bibliothèque utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="ae10f-147">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="ae10f-148">Quand vous activez cet élément, les surcharges de stratégie et de preuve fonctionnent comme dans les versions antérieures du Framework.</span><span class="sxs-lookup"><span data-stu-id="ae10f-148">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="ae10f-149">Le comportement de la stratégie CAS est spécifié par version du runtime ; la modification de la stratégie CAS pour une version du runtime n'affecte donc pas la stratégie CAS d'une autre version.</span><span class="sxs-lookup"><span data-stu-id="ae10f-149">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ae10f-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae10f-150">See also</span></span>

- [<span data-ttu-id="ae10f-151">Comment : exécuter du code de confiance partielle dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="ae10f-151">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="ae10f-152">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="ae10f-152">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
