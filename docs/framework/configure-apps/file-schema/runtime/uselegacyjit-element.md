---
title: Élément <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b783a82b1ef964de308532ef544bbfab2397400
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252224"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="ed5a1-102">\<useLegacyJit>, élément</span><span class="sxs-lookup"><span data-stu-id="ed5a1-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="ed5a1-103">Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="ed5a1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed5a1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed5a1-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed5a1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ed5a1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit>**</span><span class="sxs-lookup"><span data-stu-id="ed5a1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5a1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed5a1-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="ed5a1-108">Le nom `useLegacyJit` de l’élément respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed5a1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ed5a1-109">Attributes and elements</span></span>

<span data-ttu-id="ed5a1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed5a1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ed5a1-111">Attributes</span></span>  
  
| <span data-ttu-id="ed5a1-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ed5a1-112">Attribute</span></span> | <span data-ttu-id="ed5a1-113">Description</span><span class="sxs-lookup"><span data-stu-id="ed5a1-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="ed5a1-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-114">Required attribute.</span></span><br><br><span data-ttu-id="ed5a1-115">Spécifie si le runtime utilise le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="ed5a1-116">attribut activé</span><span class="sxs-lookup"><span data-stu-id="ed5a1-116">enabled attribute</span></span>  
  
| <span data-ttu-id="ed5a1-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="ed5a1-117">Value</span></span> | <span data-ttu-id="ed5a1-118">Description</span><span class="sxs-lookup"><span data-stu-id="ed5a1-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="ed5a1-119">0</span><span class="sxs-lookup"><span data-stu-id="ed5a1-119">0</span></span>     | <span data-ttu-id="ed5a1-120">Le common language runtime utilise le nouveau compilateur JIT 64 bits inclus dans les .NET Framework 4,6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="ed5a1-121">1</span><span class="sxs-lookup"><span data-stu-id="ed5a1-121">1</span></span>     | <span data-ttu-id="ed5a1-122">Le common language runtime utilise l’ancien compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="ed5a1-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ed5a1-123">Child elements</span></span>

<span data-ttu-id="ed5a1-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="ed5a1-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ed5a1-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ed5a1-125">Parent elements</span></span>  
  
| <span data-ttu-id="ed5a1-126">Élément</span><span class="sxs-lookup"><span data-stu-id="ed5a1-126">Element</span></span>         | <span data-ttu-id="ed5a1-127">Description</span><span class="sxs-lookup"><span data-stu-id="ed5a1-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="ed5a1-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="ed5a1-129">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="ed5a1-130">Notes</span><span class="sxs-lookup"><span data-stu-id="ed5a1-130">Remarks</span></span>  

<span data-ttu-id="ed5a1-131">À partir de la .NET Framework 4,6, le common language runtime utilise un nouveau compilateur 64 bits pour la compilation juste-à-temps (JIT) par défaut.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="ed5a1-132">Dans certains cas, cela peut entraîner une différence de comportement par rapport au code d’application qui a été compilé juste-à-temps par la version précédente du compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="ed5a1-133">En affectant `enabled` à `1`l’attribut `<useLegacyJit>` de l’élément la valeur, vous pouvez désactiver le nouveau compilateur JIT 64 bits et compiler à la place votre application à l’aide du compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed5a1-134">L' `<useLegacyJit>` élément affecte uniquement la compilation JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="ed5a1-135">La compilation avec le compilateur JIT 32 bits n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="ed5a1-136">Au lieu d’utiliser un paramètre de fichier de configuration, vous pouvez activer le compilateur JIT 64 bits hérité de deux manières :</span><span class="sxs-lookup"><span data-stu-id="ed5a1-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="ed5a1-137">Définition d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="ed5a1-137">Setting an environment variable</span></span>

  <span data-ttu-id="ed5a1-138">Affectez `COMPLUS_useLegacyJit` `1` à la variable d’environnement (utilisezlenouveaucompilateurJIT64bits)ou(utilisezl’anciencompilateurJIT64bits):`0`</span><span class="sxs-lookup"><span data-stu-id="ed5a1-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="ed5a1-139">La variable d’environnement a une *portée globale*, ce qui signifie qu’elle affecte toutes les applications exécutées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="ed5a1-140">Si elle est définie, elle peut être remplacée par le paramètre du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="ed5a1-141">Le nom de la variable d’environnement n’est pas sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="ed5a1-142">Ajout d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="ed5a1-142">Adding a registry key</span></span>

  <span data-ttu-id="ed5a1-143">Vous pouvez activer le compilateur JIT 64 bits hérité en ajoutant une `REG_DWORD` valeur à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` clé ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` dans le registre.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="ed5a1-144">La valeur est nommée `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="ed5a1-145">Si la valeur est 0, le nouveau compilateur est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="ed5a1-146">Si la valeur est 1, le compilateur JIT 64 bits hérité est activé.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="ed5a1-147">Le nom de la valeur de registre ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="ed5a1-148">L’ajout de la valeur `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` à la clé affecte toutes les applications qui s’exécutent sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="ed5a1-149">L’ajout de la valeur `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` à la clé affecte toutes les applications exécutées par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="ed5a1-150">Si un ordinateur est configuré avec plusieurs comptes d’utilisateur, seules les applications exécutées par l’utilisateur actuel sont affectées, sauf si la valeur est également ajoutée aux clés de Registre pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="ed5a1-151">L’ajout `<useLegacyJit>` de l’élément à un fichier de configuration remplace les paramètres du Registre, s’ils sont présents.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed5a1-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed5a1-152">Example</span></span>  

<span data-ttu-id="ed5a1-153">Le fichier de configuration suivant désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise à la place le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="ed5a1-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed5a1-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed5a1-154">See also</span></span>

- [<span data-ttu-id="ed5a1-155">\<Élément > du Runtime</span><span class="sxs-lookup"><span data-stu-id="ed5a1-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="ed5a1-156">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="ed5a1-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="ed5a1-157">Atténuation Nouveau compilateur JIT 64 bits</span><span class="sxs-lookup"><span data-stu-id="ed5a1-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
