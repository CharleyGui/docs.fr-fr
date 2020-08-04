---
title: Mgmtclassgen.exe (Management Strongly Typed Class Generator)
description: Comprendre Mgmtclassgen.exe, le générateur de classes fortement typées de gestion. Cet outil vous permet de générer rapidement une classe managée à liaison anticipée pour une classe WMI.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
ms.openlocfilehash: 89facd4369dad6168e46febd3e34d7f7c235faf0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517293"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="64576-104">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span><span class="sxs-lookup"><span data-stu-id="64576-104">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="64576-105">L'outil Management Strongly Typed Class Generator vous permet de générer rapidement une classe managée à liaison anticipée pour une classe WMI (Windows Management Instrumentation) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="64576-105">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="64576-106">La classe générée simplifie le code à écrire pour accéder à une instance de la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="64576-106">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64576-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="64576-107">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="64576-108">Argument</span><span class="sxs-lookup"><span data-stu-id="64576-108">Argument</span></span>|<span data-ttu-id="64576-109">Description</span><span class="sxs-lookup"><span data-stu-id="64576-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="64576-110">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="64576-110">*WMIClass*</span></span>|<span data-ttu-id="64576-111">Classe Windows Management Instrumentation pour laquelle générer une classe managée à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="64576-111">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="64576-112">Option</span><span class="sxs-lookup"><span data-stu-id="64576-112">Option</span></span>|<span data-ttu-id="64576-113">Description</span><span class="sxs-lookup"><span data-stu-id="64576-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="64576-114">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="64576-114">**/l**  *language*</span></span>|<span data-ttu-id="64576-115">Spécifie le langage à utiliser pour générer la classe managée à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="64576-115">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="64576-116">Vous pouvez spécifier **CS** (C# par défaut), **VB** (Visual Basic), **MC** (C++) ou **JS** (JScript) comme argument de langage.</span><span class="sxs-lookup"><span data-stu-id="64576-116">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="64576-117">**/m**  *machine*</span><span class="sxs-lookup"><span data-stu-id="64576-117">**/m**  *machine*</span></span>|<span data-ttu-id="64576-118">Spécifie l'ordinateur auquel se connecter, sur lequel la classe WMI se trouve.</span><span class="sxs-lookup"><span data-stu-id="64576-118">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="64576-119">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="64576-119">The default is the local computer.</span></span>|  
|<span data-ttu-id="64576-120">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="64576-120">**/n**  *path*</span></span>|<span data-ttu-id="64576-121">Spécifie le chemin vers l’espace de noms WMI qui contient la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="64576-121">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="64576-122">Si vous ne spécifiez pas cette option, l’outil génère le code pour *WMIClass* dans l’espace de noms **Root\cimv2** par défaut.</span><span class="sxs-lookup"><span data-stu-id="64576-122">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="64576-123">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="64576-123">**/o**  *classnamespace*</span></span>|<span data-ttu-id="64576-124">Spécifie l'espace de noms .NET dans lequel générer la classe de code managé.</span><span class="sxs-lookup"><span data-stu-id="64576-124">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="64576-125">Si vous ne spécifiez pas cette option, l'outil générera l'espace de noms en fonction de l'espace de noms WMI et du préfixe du schéma.</span><span class="sxs-lookup"><span data-stu-id="64576-125">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="64576-126">Le préfixe du schéma est la partie du nom de la classe qui précède le trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="64576-126">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="64576-127">Par exemple, pour la classe **Win32_OperatingSystem** qui se trouve dans l’espace de noms **Root\cimv2**, l’outil génère la classe dans **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="64576-127">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="64576-128">**/p**  *filepath*</span><span class="sxs-lookup"><span data-stu-id="64576-128">**/p**  *filepath*</span></span>|<span data-ttu-id="64576-129">Spécifie le chemin vers le fichier dans lequel le code généré sera enregistré.</span><span class="sxs-lookup"><span data-stu-id="64576-129">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="64576-130">Si vous ne spécifiez pas cette option, l'outil créera le fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="64576-130">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="64576-131">Il nomme la classe et le fichier dans lesquels il génère la classe à l’aide de l’argument *WMIClass*.</span><span class="sxs-lookup"><span data-stu-id="64576-131">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="64576-132">Les noms de la classe et du fichier sont les mêmes que ceux de *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="64576-132">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="64576-133">Si *WMIClass* contient un trait de soulignement, l’outil utilise la partie du nom de la classe qui suit le trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="64576-133">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="64576-134">Par exemple, si le nom *WMIClass* est au format **Win32_LogicalDisk**, la classe et le fichier générés sont nommés « logicaldisk ».</span><span class="sxs-lookup"><span data-stu-id="64576-134">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="64576-135">Si un fichier existe déjà, l'outil écrase le fichier existant.</span><span class="sxs-lookup"><span data-stu-id="64576-135">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="64576-136">**/pw**  *password*</span><span class="sxs-lookup"><span data-stu-id="64576-136">**/pw**  *password*</span></span>|<span data-ttu-id="64576-137">Définit le mot de passe à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.</span><span class="sxs-lookup"><span data-stu-id="64576-137">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="64576-138">**/u**  *user name*</span><span class="sxs-lookup"><span data-stu-id="64576-138">**/u**  *user name*</span></span>|<span data-ttu-id="64576-139">Définit le nom d’utilisateur à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.</span><span class="sxs-lookup"><span data-stu-id="64576-139">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="64576-140">**/?**</span><span class="sxs-lookup"><span data-stu-id="64576-140">**/?**</span></span>|<span data-ttu-id="64576-141">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="64576-141">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64576-142">Remarques</span><span class="sxs-lookup"><span data-stu-id="64576-142">Remarks</span></span>  
 <span data-ttu-id="64576-143">Mgmtclassgen.exe utilise la méthode <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="64576-143">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="64576-144">Vous pouvez donc utiliser n'importe quel fournisseur de code personnalisé pour générer le code dans des langages managés autres que C#, Visual Basic et JScript.</span><span class="sxs-lookup"><span data-stu-id="64576-144">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="64576-145">Notez que les classes générées sont liées au schéma pour lequel elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="64576-145">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="64576-146">Si le schéma sous-jacent change, vous devez régénérer la classe pour que les modifications effectuées dans le schéma soient prises en compte.</span><span class="sxs-lookup"><span data-stu-id="64576-146">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="64576-147">Le tableau suivant montre la correspondance entre les types Common Information Model (CIM) WMI et les types de données d'une classe générée :</span><span class="sxs-lookup"><span data-stu-id="64576-147">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="64576-148">Type CIM</span><span class="sxs-lookup"><span data-stu-id="64576-148">CIM type</span></span>|<span data-ttu-id="64576-149">Type de données dans la classe générée</span><span class="sxs-lookup"><span data-stu-id="64576-149">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="64576-150">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="64576-150">CIM_SINT8</span></span>|<span data-ttu-id="64576-151">**SByte**</span><span class="sxs-lookup"><span data-stu-id="64576-151">**SByte**</span></span>|  
|<span data-ttu-id="64576-152">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="64576-152">CIM_UINT8</span></span>|<span data-ttu-id="64576-153">**Poids**</span><span class="sxs-lookup"><span data-stu-id="64576-153">**Byte**</span></span>|  
|<span data-ttu-id="64576-154">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="64576-154">CIM_SINT16</span></span>|<span data-ttu-id="64576-155">**Int16**</span><span class="sxs-lookup"><span data-stu-id="64576-155">**Int16**</span></span>|  
|<span data-ttu-id="64576-156">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="64576-156">CIM_UINT16</span></span>|<span data-ttu-id="64576-157">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="64576-157">**UInt16**</span></span>|  
|<span data-ttu-id="64576-158">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="64576-158">CIM_SINT32</span></span>|<span data-ttu-id="64576-159">**Int32**</span><span class="sxs-lookup"><span data-stu-id="64576-159">**Int32**</span></span>|  
|<span data-ttu-id="64576-160">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="64576-160">SIM_UINT32</span></span>|<span data-ttu-id="64576-161">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="64576-161">**UInt32**</span></span>|  
|<span data-ttu-id="64576-162">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="64576-162">CIM_SINT64</span></span>|<span data-ttu-id="64576-163">**Int64**</span><span class="sxs-lookup"><span data-stu-id="64576-163">**Int64**</span></span>|  
|<span data-ttu-id="64576-164">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="64576-164">CIM_UINT64</span></span>|<span data-ttu-id="64576-165">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="64576-165">**UInt64**</span></span>|  
|<span data-ttu-id="64576-166">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="64576-166">CIM_REAL32</span></span>|<span data-ttu-id="64576-167">**Unique**</span><span class="sxs-lookup"><span data-stu-id="64576-167">**Single**</span></span>|  
|<span data-ttu-id="64576-168">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="64576-168">CIM_REAL64</span></span>|<span data-ttu-id="64576-169">**Double**</span><span class="sxs-lookup"><span data-stu-id="64576-169">**Double**</span></span>|  
|<span data-ttu-id="64576-170">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="64576-170">CIM_BOOLEAN</span></span>|<span data-ttu-id="64576-171">**Booléen**</span><span class="sxs-lookup"><span data-stu-id="64576-171">**Boolean**</span></span>|  
|<span data-ttu-id="64576-172">CIM_String</span><span class="sxs-lookup"><span data-stu-id="64576-172">CIM_String</span></span>|<span data-ttu-id="64576-173">**Chaîne**</span><span class="sxs-lookup"><span data-stu-id="64576-173">**String**</span></span>|  
|<span data-ttu-id="64576-174">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="64576-174">CIM_DATETIME</span></span>|<span data-ttu-id="64576-175">**DateTime** ou **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="64576-175">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="64576-176">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="64576-176">CIM_REFERENCE</span></span>|<span data-ttu-id="64576-177">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="64576-177">**ManagementPath**</span></span>|  
|<span data-ttu-id="64576-178">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="64576-178">CIM_CHAR16</span></span>|<span data-ttu-id="64576-179">**Char**</span><span class="sxs-lookup"><span data-stu-id="64576-179">**Char**</span></span>|  
|<span data-ttu-id="64576-180">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="64576-180">CIM_OBJECT</span></span>|<span data-ttu-id="64576-181">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="64576-181">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="64576-182">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="64576-182">CIM_IUNKNOWN</span></span>|<span data-ttu-id="64576-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="64576-183">**Object**</span></span>|  
|<span data-ttu-id="64576-184">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="64576-184">CIM_ARRAY</span></span>|<span data-ttu-id="64576-185">Tableau des objets mentionnés ci-dessus</span><span class="sxs-lookup"><span data-stu-id="64576-185">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="64576-186">Notez les comportements suivants lorsque vous générez une classe WMI :</span><span class="sxs-lookup"><span data-stu-id="64576-186">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="64576-187">Il est possible d'utiliser un nom de propriété ou de méthode existant pour une méthode ou une propriété standard publique.</span><span class="sxs-lookup"><span data-stu-id="64576-187">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="64576-188">Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="64576-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="64576-189">Le nom d'une propriété ou d'une méthode dans une classe générée peut être un mot clé dans le langage de programmation cible.</span><span class="sxs-lookup"><span data-stu-id="64576-189">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="64576-190">Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="64576-190">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="64576-191">Dans WMI, les qualificateurs sont des modificateurs contenant des informations qui décrivent une classe, une instance, une propriété ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="64576-191">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="64576-192">WMI utilise des qualificateurs standard, tels que **Read**, **Write** et **Key**, pour décrire une propriété dans une classe générée.</span><span class="sxs-lookup"><span data-stu-id="64576-192">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="64576-193">Par exemple, une propriété modifiée avec un qualificateur **Read** est définie uniquement avec un accesseur **get** de propriété dans la classe générée.</span><span class="sxs-lookup"><span data-stu-id="64576-193">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="64576-194">Les propriétés marquées avec un qualificateur **Read** restant en lecture seule, aucun accesseur **set** n’est défini.</span><span class="sxs-lookup"><span data-stu-id="64576-194">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="64576-195">Une propriété numérique peut être modifiée par les qualificateurs **Values** et **ValueMaps** pour indiquer que seules des valeurs autorisées et spécifiées peuvent lui être affectées.</span><span class="sxs-lookup"><span data-stu-id="64576-195">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="64576-196">Une énumération est générée avec ces qualificateurs **Values** et **ValueMaps**, et la propriété est mappée à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="64576-196">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="64576-197">WMI utilise le singleton de terme pour décrire une classe qui ne peut avoir qu'une seule instance.</span><span class="sxs-lookup"><span data-stu-id="64576-197">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="64576-198">C'est pourquoi le constructeur sans paramètre d’une classe singleton initialisera la classe à la seule instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="64576-198">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="64576-199">Une classe WMI peut avoir des objets pour propriétés.</span><span class="sxs-lookup"><span data-stu-id="64576-199">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="64576-200">Lorsque vous générez une classe fortement typée pour ce type de classe WMI, vous devez envisager de générer des classes fortement typées pour les types des propriétés de l’objet incorporé.</span><span class="sxs-lookup"><span data-stu-id="64576-200">When you generate a strongly typed class for this type of WMI class, you should consider generating strongly typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="64576-201">Cela vous permettra d’accéder aux objets incorporés de manière fortement typée.</span><span class="sxs-lookup"><span data-stu-id="64576-201">This will allow you to access the embedded objects in a strongly typed manner.</span></span> <span data-ttu-id="64576-202">Il est possible que le code généré ne puisse pas détecter le type de l'objet incorporé.</span><span class="sxs-lookup"><span data-stu-id="64576-202">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="64576-203">Dans ce cas, un commentaire sera créé dans le code généré pour vous informer de ce problème.</span><span class="sxs-lookup"><span data-stu-id="64576-203">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="64576-204">Vous pouvez alors modifier le code généré pour typer la propriété vers l'autre classe générée.</span><span class="sxs-lookup"><span data-stu-id="64576-204">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="64576-205">Dans WMI, la valeur du type de données CIM_DATETIME peut représenter soit une date ou une heure spécifique, soit un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="64576-205">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="64576-206">Si la valeur de données représente une date et une heure, le type de données de la classe générée est **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="64576-206">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="64576-207">Si la valeur de données représente un intervalle de temps, le type de données de la classe générée est **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="64576-207">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="64576-208">Vous pouvez également générer une classe fortement typée à l’aide de l’extension de gestion Explorateur de serveurs dans Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="64576-208">You can alternately generate a strongly typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="64576-209">Pour plus d’informations sur WMI, consultez la rubrique **Windows Management Instrumentation** dans la documentation du kit SDK de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="64576-209">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="64576-210">Exemples</span><span class="sxs-lookup"><span data-stu-id="64576-210">Examples</span></span>  
 <span data-ttu-id="64576-211">La commande suivante génère une classe managée en C# pour la classe WMI **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="64576-211">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="64576-212">L’outil écrit la classe managée dans le fichier source sous c:\disk.cs dans l’espace de noms **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="64576-212">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="64576-213">L'exemple de code suivant montre comment utiliser par programme une classe générée.</span><span class="sxs-lookup"><span data-stu-id="64576-213">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="64576-214">Tout d'abord, une instance de la classe est énumérée et le chemin est imprimé.</span><span class="sxs-lookup"><span data-stu-id="64576-214">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="64576-215">Ensuite, une instance de la classe générée à initialiser est créée avec une instance de WMI.</span><span class="sxs-lookup"><span data-stu-id="64576-215">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="64576-216">`Process` est la classe générée pour **Win32_Process** et `LogicalDisk` est la classe générée pour **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="64576-216">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App
   Public Shared Sub Main()
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="64576-217">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64576-217">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="64576-218">outils</span><span class="sxs-lookup"><span data-stu-id="64576-218">Tools</span></span>](index.md)
- [<span data-ttu-id="64576-219">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="64576-219">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
