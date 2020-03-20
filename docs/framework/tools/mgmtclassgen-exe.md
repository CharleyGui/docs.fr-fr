---
title: Mgmtclassgen.exe (Management Strongly Typed Class Generator)
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
ms.openlocfilehash: 5e39670fbb40acb999a243ac86683219f3c89e4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180380"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="4a604-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span><span class="sxs-lookup"><span data-stu-id="4a604-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="4a604-103">L'outil Management Strongly Typed Class Generator vous permet de générer rapidement une classe managée à liaison anticipée pour une classe WMI (Windows Management Instrumentation) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4a604-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="4a604-104">La classe générée simplifie le code à écrire pour accéder à une instance de la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="4a604-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a604-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a604-105">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="4a604-106">Argument</span><span class="sxs-lookup"><span data-stu-id="4a604-106">Argument</span></span>|<span data-ttu-id="4a604-107">Description</span><span class="sxs-lookup"><span data-stu-id="4a604-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4a604-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="4a604-108">*WMIClass*</span></span>|<span data-ttu-id="4a604-109">Classe Windows Management Instrumentation pour laquelle générer une classe managée à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="4a604-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="4a604-110">Option</span><span class="sxs-lookup"><span data-stu-id="4a604-110">Option</span></span>|<span data-ttu-id="4a604-111">Description</span><span class="sxs-lookup"><span data-stu-id="4a604-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a604-112">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="4a604-112">**/l**  *language*</span></span>|<span data-ttu-id="4a604-113">Spécifie le langage à utiliser pour générer la classe managée à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="4a604-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="4a604-114">Vous pouvez spécifier **CS** (C# par défaut), **VB** (Visual Basic), **MC** (C++) ou **JS** (JScript) comme argument de langage.</span><span class="sxs-lookup"><span data-stu-id="4a604-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="4a604-115">**/m**  *machine*</span><span class="sxs-lookup"><span data-stu-id="4a604-115">**/m**  *machine*</span></span>|<span data-ttu-id="4a604-116">Spécifie l'ordinateur auquel se connecter, sur lequel la classe WMI se trouve.</span><span class="sxs-lookup"><span data-stu-id="4a604-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="4a604-117">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4a604-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="4a604-118">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="4a604-118">**/n**  *path*</span></span>|<span data-ttu-id="4a604-119">Spécifie le chemin vers l’espace de noms WMI qui contient la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="4a604-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="4a604-120">Si vous ne spécifiez pas cette option, l’outil génère le code pour *WMIClass* dans l’espace de noms **Root\cimv2** par défaut.</span><span class="sxs-lookup"><span data-stu-id="4a604-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="4a604-121">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="4a604-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="4a604-122">Spécifie l'espace de noms .NET dans lequel générer la classe de code managé.</span><span class="sxs-lookup"><span data-stu-id="4a604-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="4a604-123">Si vous ne spécifiez pas cette option, l'outil générera l'espace de noms en fonction de l'espace de noms WMI et du préfixe du schéma.</span><span class="sxs-lookup"><span data-stu-id="4a604-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="4a604-124">Le préfixe du schéma est la partie du nom de la classe qui précède le trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="4a604-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="4a604-125">Par exemple, pour la classe **Win32_OperatingSystem** qui se trouve dans l’espace de noms **Root\cimv2**, l’outil génère la classe dans **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="4a604-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="4a604-126">**/p**  *filepath*</span><span class="sxs-lookup"><span data-stu-id="4a604-126">**/p**  *filepath*</span></span>|<span data-ttu-id="4a604-127">Spécifie le chemin vers le fichier dans lequel le code généré sera enregistré.</span><span class="sxs-lookup"><span data-stu-id="4a604-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="4a604-128">Si vous ne spécifiez pas cette option, l'outil créera le fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a604-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="4a604-129">Il nomme la classe et le fichier dans lesquels il génère la classe à l’aide de l’argument *WMIClass*.</span><span class="sxs-lookup"><span data-stu-id="4a604-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="4a604-130">Les noms de la classe et du fichier sont les mêmes que ceux de *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="4a604-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="4a604-131">Si *WMIClass* contient un trait de soulignement, l’outil utilise la partie du nom de la classe qui suit le trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="4a604-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="4a604-132">Par exemple, si le nom *WMIClass* est au format **Win32_LogicalDisk**, la classe et le fichier générés sont nommés « logicaldisk ».</span><span class="sxs-lookup"><span data-stu-id="4a604-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="4a604-133">Si un fichier existe déjà, l'outil écrase le fichier existant.</span><span class="sxs-lookup"><span data-stu-id="4a604-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="4a604-134">**/pw**  *password*</span><span class="sxs-lookup"><span data-stu-id="4a604-134">**/pw**  *password*</span></span>|<span data-ttu-id="4a604-135">Définit le mot de passe à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.</span><span class="sxs-lookup"><span data-stu-id="4a604-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="4a604-136">**/u**  *user name*</span><span class="sxs-lookup"><span data-stu-id="4a604-136">**/u**  *user name*</span></span>|<span data-ttu-id="4a604-137">Définit le nom d’utilisateur à utiliser quand vous vous connectez à un ordinateur spécifié par l’option **/m**.</span><span class="sxs-lookup"><span data-stu-id="4a604-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="4a604-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="4a604-138">**/?**</span></span>|<span data-ttu-id="4a604-139">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="4a604-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a604-140">Notes </span><span class="sxs-lookup"><span data-stu-id="4a604-140">Remarks</span></span>  
 <span data-ttu-id="4a604-141">Mgmtclassgen.exe utilise la méthode <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a604-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4a604-142">Vous pouvez donc utiliser n'importe quel fournisseur de code personnalisé pour générer le code dans des langages managés autres que C#, Visual Basic et JScript.</span><span class="sxs-lookup"><span data-stu-id="4a604-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="4a604-143">Notez que les classes générées sont liées au schéma pour lequel elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="4a604-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="4a604-144">Si le schéma sous-jacent change, vous devez régénérer la classe pour que les modifications effectuées dans le schéma soient prises en compte.</span><span class="sxs-lookup"><span data-stu-id="4a604-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="4a604-145">Le tableau suivant montre la correspondance entre les types Common Information Model (CIM) WMI et les types de données d'une classe générée :</span><span class="sxs-lookup"><span data-stu-id="4a604-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="4a604-146">Type CIM</span><span class="sxs-lookup"><span data-stu-id="4a604-146">CIM type</span></span>|<span data-ttu-id="4a604-147">Type de données dans la classe générée</span><span class="sxs-lookup"><span data-stu-id="4a604-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="4a604-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="4a604-148">CIM_SINT8</span></span>|<span data-ttu-id="4a604-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="4a604-149">**SByte**</span></span>|  
|<span data-ttu-id="4a604-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="4a604-150">CIM_UINT8</span></span>|<span data-ttu-id="4a604-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="4a604-151">**Byte**</span></span>|  
|<span data-ttu-id="4a604-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="4a604-152">CIM_SINT16</span></span>|<span data-ttu-id="4a604-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="4a604-153">**Int16**</span></span>|  
|<span data-ttu-id="4a604-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="4a604-154">CIM_UINT16</span></span>|<span data-ttu-id="4a604-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="4a604-155">**UInt16**</span></span>|  
|<span data-ttu-id="4a604-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="4a604-156">CIM_SINT32</span></span>|<span data-ttu-id="4a604-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="4a604-157">**Int32**</span></span>|  
|<span data-ttu-id="4a604-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="4a604-158">SIM_UINT32</span></span>|<span data-ttu-id="4a604-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="4a604-159">**UInt32**</span></span>|  
|<span data-ttu-id="4a604-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="4a604-160">CIM_SINT64</span></span>|<span data-ttu-id="4a604-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="4a604-161">**Int64**</span></span>|  
|<span data-ttu-id="4a604-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="4a604-162">CIM_UINT64</span></span>|<span data-ttu-id="4a604-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="4a604-163">**UInt64**</span></span>|  
|<span data-ttu-id="4a604-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="4a604-164">CIM_REAL32</span></span>|<span data-ttu-id="4a604-165">**Seul**</span><span class="sxs-lookup"><span data-stu-id="4a604-165">**Single**</span></span>|  
|<span data-ttu-id="4a604-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="4a604-166">CIM_REAL64</span></span>|<span data-ttu-id="4a604-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="4a604-167">**Double**</span></span>|  
|<span data-ttu-id="4a604-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="4a604-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="4a604-169">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="4a604-169">**Boolean**</span></span>|  
|<span data-ttu-id="4a604-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="4a604-170">CIM_String</span></span>|<span data-ttu-id="4a604-171">**Chaîne**</span><span class="sxs-lookup"><span data-stu-id="4a604-171">**String**</span></span>|  
|<span data-ttu-id="4a604-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="4a604-172">CIM_DATETIME</span></span>|<span data-ttu-id="4a604-173">**DateTime** ou **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="4a604-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="4a604-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="4a604-174">CIM_REFERENCE</span></span>|<span data-ttu-id="4a604-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="4a604-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="4a604-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="4a604-176">CIM_CHAR16</span></span>|<span data-ttu-id="4a604-177">**Char Char**</span><span class="sxs-lookup"><span data-stu-id="4a604-177">**Char**</span></span>|  
|<span data-ttu-id="4a604-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="4a604-178">CIM_OBJECT</span></span>|<span data-ttu-id="4a604-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="4a604-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="4a604-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="4a604-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="4a604-181">**Objet**</span><span class="sxs-lookup"><span data-stu-id="4a604-181">**Object**</span></span>|  
|<span data-ttu-id="4a604-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="4a604-182">CIM_ARRAY</span></span>|<span data-ttu-id="4a604-183">Tableau des objets mentionnés ci-dessus</span><span class="sxs-lookup"><span data-stu-id="4a604-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="4a604-184">Notez les comportements suivants lorsque vous générez une classe WMI :</span><span class="sxs-lookup"><span data-stu-id="4a604-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="4a604-185">Il est possible d'utiliser un nom de propriété ou de méthode existant pour une méthode ou une propriété standard publique.</span><span class="sxs-lookup"><span data-stu-id="4a604-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="4a604-186">Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="4a604-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="4a604-187">Le nom d'une propriété ou d'une méthode dans une classe générée peut être un mot clé dans le langage de programmation cible.</span><span class="sxs-lookup"><span data-stu-id="4a604-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="4a604-188">Dans ce cas, l'outil modifie le nom de la propriété ou de la méthode dans la classe générée pour éviter les conflits dans l'affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="4a604-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="4a604-189">Dans WMI, les qualificateurs sont des modificateurs contenant des informations qui décrivent une classe, une instance, une propriété ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="4a604-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="4a604-190">WMI utilise des qualificateurs standard, tels que **Read**, **Write** et **Key**, pour décrire une propriété dans une classe générée.</span><span class="sxs-lookup"><span data-stu-id="4a604-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="4a604-191">Par exemple, une propriété modifiée avec un qualificateur **Read** est définie uniquement avec un accesseur **get** de propriété dans la classe générée.</span><span class="sxs-lookup"><span data-stu-id="4a604-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="4a604-192">Les propriétés marquées avec un qualificateur **Read** restant en lecture seule, aucun accesseur **set** n’est défini.</span><span class="sxs-lookup"><span data-stu-id="4a604-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="4a604-193">Une propriété numérique peut être modifiée par les qualificateurs **Values** et **ValueMaps** pour indiquer que seules des valeurs autorisées et spécifiées peuvent lui être affectées.</span><span class="sxs-lookup"><span data-stu-id="4a604-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="4a604-194">Une énumération est générée avec ces qualificateurs **Values** et **ValueMaps**, et la propriété est mappée à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="4a604-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="4a604-195">WMI utilise le singleton de terme pour décrire une classe qui ne peut avoir qu'une seule instance.</span><span class="sxs-lookup"><span data-stu-id="4a604-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="4a604-196">C'est pourquoi le constructeur sans paramètre d’une classe singleton initialisera la classe à la seule instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="4a604-196">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="4a604-197">Une classe WMI peut avoir des objets pour propriétés.</span><span class="sxs-lookup"><span data-stu-id="4a604-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="4a604-198">Lorsque vous générez une classe fortement typée pour ce type de classe WMI, n'oubliez pas de générer également des classes fortement typées pour les types des propriétés de l'objet incorporé.</span><span class="sxs-lookup"><span data-stu-id="4a604-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="4a604-199">Cela vous permettra d'accéder aux objets incorporés de manière fortement typée.</span><span class="sxs-lookup"><span data-stu-id="4a604-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="4a604-200">Il est possible que le code généré ne puisse pas détecter le type de l'objet incorporé.</span><span class="sxs-lookup"><span data-stu-id="4a604-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="4a604-201">Dans ce cas, un commentaire sera créé dans le code généré pour vous informer de ce problème.</span><span class="sxs-lookup"><span data-stu-id="4a604-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="4a604-202">Vous pouvez alors modifier le code généré pour typer la propriété vers l'autre classe générée.</span><span class="sxs-lookup"><span data-stu-id="4a604-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="4a604-203">Dans WMI, la valeur du type de données CIM_DATETIME peut représenter soit une date ou une heure spécifique, soit un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="4a604-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="4a604-204">Si la valeur de données représente une date et une heure, le type de données de la classe générée est **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="4a604-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="4a604-205">Si la valeur de données représente un intervalle de temps, le type de données de la classe générée est **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="4a604-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="4a604-206">Vous pouvez également générer une classe fortement typée à l’aide de l’extension de gestion de l’Explorateur de serveurs de Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="4a604-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="4a604-207">Pour plus d’informations sur WMI, consultez la rubrique **Windows Management Instrumentation** dans la documentation du kit SDK de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="4a604-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4a604-208">Exemples</span><span class="sxs-lookup"><span data-stu-id="4a604-208">Examples</span></span>  
 <span data-ttu-id="4a604-209">La commande suivante génère une classe managée en C# pour la classe WMI **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="4a604-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="4a604-210">L’outil écrit la classe managée dans le fichier source sous c:\disk.cs dans l’espace de noms **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="4a604-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="4a604-211">L'exemple de code suivant montre comment utiliser par programme une classe générée.</span><span class="sxs-lookup"><span data-stu-id="4a604-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="4a604-212">Tout d'abord, une instance de la classe est énumérée et le chemin est imprimé.</span><span class="sxs-lookup"><span data-stu-id="4a604-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="4a604-213">Ensuite, une instance de la classe générée à initialiser est créée avec une instance de WMI.</span><span class="sxs-lookup"><span data-stu-id="4a604-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="4a604-214">`Process` est la classe générée pour **Win32_Process** et `LogicalDisk` est la classe générée pour **Win32_LogicalDisk** dans l’espace de noms **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="4a604-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a604-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a604-215">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="4a604-216">Outils</span><span class="sxs-lookup"><span data-stu-id="4a604-216">Tools</span></span>](index.md)
- [<span data-ttu-id="4a604-217">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="4a604-217">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
