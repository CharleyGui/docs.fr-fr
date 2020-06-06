---
title: Élément <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968858"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="32c52-102">Élément \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="32c52-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="32c52-103">Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="32c52-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="32c52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32c52-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="32c52-105">Le nom de l’élément `useLegacyJit` respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="32c52-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c52-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="32c52-106">Attributes and elements</span></span>

<span data-ttu-id="32c52-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="32c52-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c52-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="32c52-108">Attributes</span></span>  
  
| <span data-ttu-id="32c52-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="32c52-109">Attribute</span></span> | <span data-ttu-id="32c52-110">Description</span><span class="sxs-lookup"><span data-stu-id="32c52-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="32c52-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="32c52-111">Required attribute.</span></span><br><br><span data-ttu-id="32c52-112">Spécifie si le runtime utilise le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="32c52-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="32c52-113">attribut activé</span><span class="sxs-lookup"><span data-stu-id="32c52-113">enabled attribute</span></span>  
  
| <span data-ttu-id="32c52-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="32c52-114">Value</span></span> | <span data-ttu-id="32c52-115">Description</span><span class="sxs-lookup"><span data-stu-id="32c52-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="32c52-116">0</span><span class="sxs-lookup"><span data-stu-id="32c52-116">0</span></span>     | <span data-ttu-id="32c52-117">Le common language runtime utilise le nouveau compilateur JIT 64 bits inclus dans les .NET Framework 4,6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="32c52-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="32c52-118">1</span><span class="sxs-lookup"><span data-stu-id="32c52-118">1</span></span>     | <span data-ttu-id="32c52-119">Le common language runtime utilise l’ancien compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="32c52-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="32c52-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="32c52-120">Child elements</span></span>

<span data-ttu-id="32c52-121">Aucune</span><span class="sxs-lookup"><span data-stu-id="32c52-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="32c52-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="32c52-122">Parent elements</span></span>  
  
| <span data-ttu-id="32c52-123">Élément</span><span class="sxs-lookup"><span data-stu-id="32c52-123">Element</span></span>         | <span data-ttu-id="32c52-124">Description</span><span class="sxs-lookup"><span data-stu-id="32c52-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="32c52-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32c52-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="32c52-126">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="32c52-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="32c52-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="32c52-127">Remarks</span></span>  

<span data-ttu-id="32c52-128">À partir de la .NET Framework 4,6, le common language runtime utilise un nouveau compilateur 64 bits pour la compilation juste-à-temps (JIT) par défaut.</span><span class="sxs-lookup"><span data-stu-id="32c52-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="32c52-129">Dans certains cas, cela peut entraîner une différence de comportement par rapport au code d’application qui a été compilé juste-à-temps par la version précédente du compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="32c52-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="32c52-130">En affectant `enabled` à l’attribut de l’élément la valeur `<useLegacyJit>` `1` , vous pouvez désactiver le nouveau compilateur JIT 64 bits et compiler à la place votre application à l’aide du compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="32c52-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32c52-131">L' `<useLegacyJit>` élément affecte uniquement la compilation JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="32c52-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="32c52-132">La compilation avec le compilateur JIT 32 bits n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="32c52-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="32c52-133">Au lieu d’utiliser un paramètre de fichier de configuration, vous pouvez activer le compilateur JIT 64 bits hérité de deux manières :</span><span class="sxs-lookup"><span data-stu-id="32c52-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="32c52-134">Définition d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="32c52-134">Setting an environment variable</span></span>

  <span data-ttu-id="32c52-135">Affectez `COMPLUS_useLegacyJit` à la variable d’environnement `0` (utilisez le nouveau compilateur JIT 64 bits) ou `1` (utilisez l’ancien compilateur JIT 64 bits) :</span><span class="sxs-lookup"><span data-stu-id="32c52-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="32c52-136">La variable d’environnement a une *portée globale*, ce qui signifie qu’elle affecte toutes les applications exécutées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c52-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="32c52-137">Si elle est définie, elle peut être remplacée par le paramètre du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="32c52-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="32c52-138">Le nom de la variable d’environnement n’est pas sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="32c52-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="32c52-139">Ajout d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="32c52-139">Adding a registry key</span></span>

  <span data-ttu-id="32c52-140">Vous pouvez activer le compilateur JIT 64 bits hérité en ajoutant une `REG_DWORD` valeur à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé ou dans le registre.</span><span class="sxs-lookup"><span data-stu-id="32c52-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="32c52-141">La valeur est nommée `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="32c52-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="32c52-142">Si la valeur est 0, le nouveau compilateur est utilisé.</span><span class="sxs-lookup"><span data-stu-id="32c52-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="32c52-143">Si la valeur est 1, le compilateur JIT 64 bits hérité est activé.</span><span class="sxs-lookup"><span data-stu-id="32c52-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="32c52-144">Le nom de la valeur de registre ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="32c52-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="32c52-145">L’ajout de la valeur à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications qui s’exécutent sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c52-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="32c52-146">L’ajout de la valeur à la `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications exécutées par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="32c52-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="32c52-147">Si un ordinateur est configuré avec plusieurs comptes d’utilisateur, seules les applications exécutées par l’utilisateur actuel sont affectées, sauf si la valeur est également ajoutée aux clés de Registre pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="32c52-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="32c52-148">L’ajout `<useLegacyJit>` de l’élément à un fichier de configuration remplace les paramètres du Registre, s’ils sont présents.</span><span class="sxs-lookup"><span data-stu-id="32c52-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c52-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="32c52-149">Example</span></span>  

<span data-ttu-id="32c52-150">Le fichier de configuration suivant désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise à la place le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="32c52-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32c52-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32c52-151">See also</span></span>

- [<span data-ttu-id="32c52-152">\<runtime>Appartient</span><span class="sxs-lookup"><span data-stu-id="32c52-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="32c52-153">\<configuration>Appartient</span><span class="sxs-lookup"><span data-stu-id="32c52-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="32c52-154">Atténuation : nouveau compilateur JIT 64 bits</span><span class="sxs-lookup"><span data-stu-id="32c52-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
