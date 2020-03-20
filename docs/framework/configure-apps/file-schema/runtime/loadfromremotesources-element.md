---
title: Élément <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154060"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="62597-102">\<chargeDeRemoteSources> élément</span><span class="sxs-lookup"><span data-stu-id="62597-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="62597-103">Précise si les assemblages chargés de sources éloignées devraient bénéficier d’une pleine confiance dans le cadre .NET 4 et plus tard.</span><span class="sxs-lookup"><span data-stu-id="62597-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62597-104">Si vous avez été dirigé vers cet article en raison d’un message d’erreur dans la liste d’erreurs du projet Visual Studio ou d’une erreur de build, voir [Comment : Utilisez une assemblée à partir du Web dans Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="62597-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="62597-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62597-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62597-106">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="62597-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="62597-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<chargeDeRemoteSources>**</span><span class="sxs-lookup"><span data-stu-id="62597-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62597-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62597-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62597-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="62597-109">Attributes and elements</span></span>
 <span data-ttu-id="62597-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="62597-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62597-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="62597-111">Attributes</span></span>  
  
|<span data-ttu-id="62597-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="62597-112">Attribute</span></span>|<span data-ttu-id="62597-113">Description</span><span class="sxs-lookup"><span data-stu-id="62597-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="62597-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="62597-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="62597-115">Précise si un assemblage chargé à partir d’une source éloignée doit bénéficier d’une pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="62597-116">attribut activé</span><span class="sxs-lookup"><span data-stu-id="62597-116">enabled attribute</span></span>  
  
|<span data-ttu-id="62597-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="62597-117">Value</span></span>|<span data-ttu-id="62597-118">Description</span><span class="sxs-lookup"><span data-stu-id="62597-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="62597-119">N’accordez pas la pleine confiance aux demandes provenant de sources éloignées.</span><span class="sxs-lookup"><span data-stu-id="62597-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="62597-120">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="62597-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="62597-121">Accorder une confiance totale aux demandes provenant de sources éloignées.</span><span class="sxs-lookup"><span data-stu-id="62597-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62597-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="62597-122">Child elements</span></span>  
 <span data-ttu-id="62597-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="62597-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62597-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="62597-124">Parent elements</span></span>  
  
|<span data-ttu-id="62597-125">Élément</span><span class="sxs-lookup"><span data-stu-id="62597-125">Element</span></span>|<span data-ttu-id="62597-126">Description</span><span class="sxs-lookup"><span data-stu-id="62597-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="62597-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62597-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="62597-128">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="62597-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62597-129">Notes </span><span class="sxs-lookup"><span data-stu-id="62597-129">Remarks</span></span>

<span data-ttu-id="62597-130">Dans le cadre .NET 3.5 et les versions antérieures, si vous chargez un assemblage à partir d’un emplacement éloigné, le code dans l’assemblage fonctionne en fiducie partielle avec un ensemble de subvention qui dépend de la zone à partir de laquelle il est chargé.</span><span class="sxs-lookup"><span data-stu-id="62597-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="62597-131">Par exemple, si vous chargez un assemblage à partir d’un site Web, il est chargé dans la zone Internet et accordé l’ensemble d’autorisation Internet.</span><span class="sxs-lookup"><span data-stu-id="62597-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="62597-132">En d’autres termes, il s’exécute dans un bac à sable Internet.</span><span class="sxs-lookup"><span data-stu-id="62597-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="62597-133">En commençant par le cadre .NET 4, la politique de sécurité d’accès au code (CAS) est désactivée et les assemblages sont chargés en pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="62597-134">Normalement, cela accorderait une pleine confiance aux <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> assemblées chargées de la méthode qui avait déjà été bacée à sable.</span><span class="sxs-lookup"><span data-stu-id="62597-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="62597-135">Pour éviter cela, la possibilité d’exécuter le code dans les assemblages chargés à partir d’une source distante est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="62597-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="62597-136">Par défaut, si vous essayez de <xref:System.IO.FileLoadException> charger un assemblage à distance, un message à l’exception comme ce qui suit est lancé :</span><span class="sxs-lookup"><span data-stu-id="62597-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="62597-137">Pour charger l’assemblage et exécuter son code, vous devez soit :</span><span class="sxs-lookup"><span data-stu-id="62597-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="62597-138">Créez explicitement un bac à sable pour l’assemblage (voir [Comment : Exécuter le code partiellement fiable dans un bac à sable).](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)</span><span class="sxs-lookup"><span data-stu-id="62597-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="62597-139">Exécutez le code de l’assemblée en pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="62597-140">Vous le faites en `<loadFromRemoteSources>` configurant l’élément.</span><span class="sxs-lookup"><span data-stu-id="62597-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="62597-141">Il vous permet de spécifier que les assemblées qui fonctionnent en partie en fiducie partielle dans les versions antérieures du cadre .NET fonctionnent maintenant en pleine confiance dans le cadre .NET 4 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="62597-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62597-142">Si l’assemblage ne doit pas fonctionner en pleine confiance, ne définissez pas cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="62597-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="62597-143">Au lieu de cela, créer un bac à sable <xref:System.AppDomain> dans lequel charger l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="62597-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="62597-144">L’attribut `enabled` `<loadFromRemoteSources>` de l’élément n’est efficace que lorsque la sécurité d’accès au code (CAS) est désactivée.</span><span class="sxs-lookup"><span data-stu-id="62597-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="62597-145">Par défaut, la politique de la SAE est désactivée dans le cadre .NET 4 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="62597-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="62597-146">Si vous `enabled` `true`vous fixez, les assemblages à distance sont accordés pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="62597-147">Si `enabled` elle n’est pas réglée à `true`, a <xref:System.IO.FileLoadException> est jeté sous l’une ou l’autre des conditions suivantes:</span><span class="sxs-lookup"><span data-stu-id="62597-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="62597-148">Le comportement de sandboxing du domaine actuel est différent de son comportement dans le cadre .NET 3.5.</span><span class="sxs-lookup"><span data-stu-id="62597-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="62597-149">Cela exige que la politique de la SAE soit désactivée, et que le domaine actuel ne soit pas bac à sable.</span><span class="sxs-lookup"><span data-stu-id="62597-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="62597-150">L’assemblage chargé n’est pas de la `MyComputer` zone.</span><span class="sxs-lookup"><span data-stu-id="62597-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="62597-151">Définir `<loadFromRemoteSources>` l’élément pour `true` empêcher cette exception d’être jeté.</span><span class="sxs-lookup"><span data-stu-id="62597-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="62597-152">Il vous permet de spécifier que vous ne vous fiez pas à l’heure courante pour poncer les assemblages chargés pour la sécurité, et qu’ils peuvent être autorisés à exécuter en pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="62597-153">Notes</span><span class="sxs-lookup"><span data-stu-id="62597-153">Notes</span></span>

- <span data-ttu-id="62597-154">Dans le cadre .NET 4.5 et les versions ultérieures, les assemblages sur les actions de réseau local fonctionnent en pleine confiance par défaut; vous n’avez pas `<loadFromRemoteSources>` à activer l’élément.</span><span class="sxs-lookup"><span data-stu-id="62597-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="62597-155">Si une application a été copiée sur le Web, elle est signalée par Windows comme étant une application web, même si elle réside sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="62597-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="62597-156">Vous pouvez modifier cette désignation en modifiant ses `<loadFromRemoteSources>` propriétés de fichiers, ou vous pouvez utiliser l’élément pour accorder à l’assemblée la pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="62597-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="62597-157">Comme alternative, vous pouvez <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> utiliser la méthode pour charger un assemblage local que le système d’exploitation a signalé comme ayant été chargé à partir du Web.</span><span class="sxs-lookup"><span data-stu-id="62597-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="62597-158">Vous pouvez <xref:System.IO.FileLoadException> obtenir une application dans une application qui est en cours d’exécution dans une application Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="62597-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="62597-159">Cela peut se produire lorsque vous essayez de charger un fichier à partir de dossiers liés sur l’ordinateur d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="62597-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="62597-160">Il peut également se produire lorsque vous essayez de charger un fichier à partir d’un dossier lié sur [les services de bureau à distance](/windows/win32/termserv/terminal-services-portal) (Services terminaux).</span><span class="sxs-lookup"><span data-stu-id="62597-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="62597-161">Pour éviter l’exception, définissez `enabled` `true`à .</span><span class="sxs-lookup"><span data-stu-id="62597-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="62597-162">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="62597-162">Configuration file</span></span>

<span data-ttu-id="62597-163">Cet élément est généralement utilisé dans le fichier de configuration d’application, mais peut être utilisé dans d’autres fichiers de configuration en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="62597-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="62597-164">Pour plus d’informations, voir l’article [Plus implicite Utilise de la politique casS: loadDeRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) dans le blog .NET Security.</span><span class="sxs-lookup"><span data-stu-id="62597-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="62597-165"> Exemple</span><span class="sxs-lookup"><span data-stu-id="62597-165">Example</span></span>

<span data-ttu-id="62597-166">L’exemple suivant montre comment accorder une pleine confiance aux assemblées chargées de sources éloignées.</span><span class="sxs-lookup"><span data-stu-id="62597-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="62597-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62597-167">See also</span></span>

- [<span data-ttu-id="62597-168">Utilisations implicites de la politique de la SAE : chargeDeRemoteSources</span><span class="sxs-lookup"><span data-stu-id="62597-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="62597-169">Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)</span><span class="sxs-lookup"><span data-stu-id="62597-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="62597-170">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="62597-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="62597-171">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="62597-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
