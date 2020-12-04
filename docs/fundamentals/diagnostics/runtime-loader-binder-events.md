---
title: Événements de Runtime de chargeur et de Binder
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques au chargeur et aux événements ETW du Binder, qui collectent des informations sur le chargeur et le Binder d’assembly.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588665"
---
# <a name="net-runtime-loader-and-binder-events"></a>Événements de chargeur et de Binder du Runtime .NET

Ces événements recueillent des informations concernant le chargement et le déchargement des assemblys et des modules. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|151|Déclenché quand un module est chargé pour un domaine d'application.|

## <a name="moduleload_v2-event"></a>Événement ModuleLoad_V2

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|152|Déclenché quand un module est chargé pendant la durée de vie d'un processus.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|ID unique du module.|
|`AssemblyID`|`win:UInt64`|ID de l'assembly dans lequel ce module réside.|
|`ModuleFlags`|`win:UInt32`|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|
|`Reserved1`|`win:UInt32`|Champ réservé.|
|`ModuleILPath`|`win:UnicodeString`|Chemin de l’image Common Intermediate Language (CIL) du module ou nom du module dynamique s’il s’agit d’un assembly dynamique (se terminant par null).|
|`ModuleNativePath`|`win:UnicodeString`|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|
|`ManagedPdbSignature`|`win:GUID`|Signature GUID de la base de données du programme géré (PDB) qui correspond à ce module.|
|`ManagedPdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit sur le fichier PDB managé qui correspond à ce module.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB managé qui correspond à ce module a été créé. Dans certains cas, cela peut simplement être un nom de fichier.|
|`NativePdbSignature`|`win:GUID`|Signature GUID du fichier PDB de Native Image Generator (NGen) correspondant à ce module, le cas échéant.|
|`NativePdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit dans le fichier PDB NGen qui correspond à ce module, le cas échéant.|
|`NativePdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB NGen qui correspond à ce module a été créé, le cas échéant. Dans certains cas, cela peut simplement être un nom de fichier.|

## <a name="moduleunload_v2-event"></a>Événement ModuleUnload_V2

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|153|Déclenché quand un module est déchargé pendant la durée de vie d'un processus.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|ID unique du module.|
|`AssemblyID`|`win:UInt64`|ID de l'assembly dans lequel ce module réside.|
|`ModuleFlags`|`win:UInt32`|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|
|`Reserved1`|`win:UInt32`|Champ réservé.|
|`ModuleILPath`|`win:UnicodeString`|Chemin de l’image Common Intermediate Language (CIL) du module ou nom du module dynamique s’il s’agit d’un assembly dynamique (se terminant par null).|
|`ModuleNativePath`|`win:UnicodeString`|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|
|`ClrInstanceID`|``win:UInt16``|ID unique de l'instance de CLR ou CoreCLR.|
|`ManagedPdbSignature`|`win:GUID`|Signature GUID de la base de données du programme géré (PDB) qui correspond à ce module.|
|`ManagedPdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit sur le fichier PDB managé qui correspond à ce module.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB managé qui correspond à ce module a été créé. Dans certains cas, cela peut simplement être un nom de fichier.|
|`NativePdbSignature`|`win:GUID`|Signature GUID du fichier PDB de Native Image Generator (NGen) correspondant à ce module, le cas échéant.|
|`NativePdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit dans le fichier PDB NGen qui correspond à ce module, le cas échéant.|
|`NativePdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB NGen qui correspond à ce module a été créé, le cas échéant. Dans certains cas, cela peut simplement être un nom de fichier.|

## <a name="moduledcstart_v2-event"></a>Événement ModuleDCStart_V2

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)

|Événement|ID de l’événement|Description
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|153|Énumère les modules pendant un arrêt de début.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|ID unique du module.|
|`AssemblyID`|`win:UInt64`|ID de l'assembly dans lequel ce module réside.|
|`ModuleFlags`|`win:UInt32`|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|
|`Reserved1`|`win:UInt32`|Champ réservé.|
|`ModuleILPath`|`win:UnicodeString`|Chemin de l’image Common Intermediate Language (CIL) du module ou nom du module dynamique s’il s’agit d’un assembly dynamique (se terminant par null).|
|`ModuleNativePath`|`win:UnicodeString`|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|
|`ManagedPdbSignature`|`win:GUID`|Signature GUID de la base de données du programme géré (PDB) qui correspond à ce module.|
|`ManagedPdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit sur le fichier PDB managé qui correspond à ce module.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB managé qui correspond à ce module a été créé. Dans certains cas, cela peut simplement être un nom de fichier.|
|`NativePdbSignature`|`win:GUID`|Signature GUID du fichier PDB de Native Image Generator (NGen) correspondant à ce module, le cas échéant.|
|`NativePdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit dans le fichier PDB NGen qui correspond à ce module, le cas échéant.|
|`NativePdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB NGen qui correspond à ce module a été créé, le cas échéant. Dans certains cas, cela peut simplement être un nom de fichier.|

## <a name="moduledcend_v2-event"></a>Événement ModuleDCEnd_V2

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|154|Énumère les modules pendant un arrêt de fin.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|ID unique du module.|
|`AssemblyID`|`win:UInt64`|ID de l'assembly dans lequel ce module réside.|
|`ModuleFlags`|`win:UInt32`|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|
|`Reserved1`|`win:UInt32`|Champ réservé.|
|`ModuleILPath`|`win:UnicodeString`|Chemin de l’image Common Intermediate Language (CIL) du module ou nom du module dynamique s’il s’agit d’un assembly dynamique (se terminant par null).|
|`ModuleNativePath`|`win:UnicodeString`|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|
|`ManagedPdbSignature`|`win:GUID`|Signature GUID de la base de données du programme géré (PDB) qui correspond à ce module.|
|`ManagedPdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit sur le fichier PDB managé qui correspond à ce module.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB managé qui correspond à ce module a été créé. Dans certains cas, cela peut simplement être un nom de fichier.|
|`NativePdbSignature`|`win:GUID`|Signature GUID du fichier PDB de Native Image Generator (NGen) correspondant à ce module, le cas échéant.|
|`NativePdbAge`|`win:UInt32`|Nombre relatif à l’âge écrit dans le fichier PDB NGen qui correspond à ce module, le cas échéant.|
|`NativePdbBuildPath`|`win:UnicodeString`|Chemin d'accès à l'emplacement où le fichier PDB NGen qui correspond à ce module a été créé, le cas échéant. Dans certains cas, cela peut simplement être un nom de fichier.|

## <a name="assemblyload_v1-event"></a>Événement AssemblyLoad_V1

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|154|Déclenché quand un assembly est chargé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|ID unique de l'assembly.|
|`AppDomainID`|`win:UInt64`|ID du domaine de cet assembly.|
|`BindingID`|`win:UInt64`|ID qui identifie de façon unique la liaison d'assembly.|
|`AssemblyFlags`|`win:UInt32`|0x1 : assembly indépendant du domaine.<br /><br /> 0x2 : assembly dynamique.<br /><br /> 0x4 : l’assembly possède une image native.<br /><br /> 0x8 : assembly pouvant être collecté.|
|`AssemblyName`|`win:UnicodeString`|Nom qualifié complet de l'assembly.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.

## <a name="assemblyunload_v1-event"></a>Événement AssemblyUnload_V1

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|155|Déclenché quand un assembly est chargé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|ID unique de l'assembly.|
|`AppDomainID`|`win:UInt64`|ID du domaine de cet assembly.|
|`BindingID`|`win:UInt64`|ID qui identifie de façon unique la liaison d'assembly.|
|`AssemblyFlags`|`win:UInt32`|0x1 : assembly indépendant du domaine.<br /><br /> 0x2 : assembly dynamique.<br /><br /> 0x4 : l’assembly possède une image native.<br /><br /> 0x8 : assembly pouvant être collecté.|
|`AssemblyName`|`win:UnicodeString`|Nom qualifié complet de l'assembly.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="assemblydcstart_v1-event"></a>Événement AssemblyDCStart_V1

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|155|Énumère les assemblys pendant un arrêt de début.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|ID unique de l'assembly.|
|`AppDomainID`|`win:UInt64`|ID du domaine de cet assembly.|
|`BindingID`|`win:UInt64`|ID qui identifie de façon unique la liaison d'assembly.|
|`AssemblyFlags`|`win:UInt32`|0x1 : assembly indépendant du domaine.<br /><br /> 0x2 : assembly dynamique.<br /><br /> 0x4 : l’assembly possède une image native.<br /><br /> 0x8 : assembly pouvant être collecté.|
|`AssemblyName`|`win:UnicodeString`|Nom qualifié complet de l'assembly.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="assemblyloadstart-event"></a>Événement AssemblyLoadStart

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|`AssemblyLoadStart`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|290|Une charge d’assembly a été demandée.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`AssemblyPath`|`win:UnicodeString`|Chemin d’accès du nom de l’assembly.|
|`RequestingAssembly`|`win:UnicodeString`|Nom de l’assembly à l’origine de la demande ("parent").|
|`AssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly.|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly (« parent ») à l’origine de la demande.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="assemblyloadstop-event"></a>Événement AssemblyLoadStop

|Mot clé pour déclencher l'événement|Événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|`AssemblyLoadStart`|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|291|Une charge d’assembly a été demandée.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`AssemblyPath`|`win:UnicodeString`|Chemin d’accès du nom de l’assembly.|
|`RequestingAssembly`|`win:UnicodeString`|Nom de l’assembly à l’origine de la demande ("parent").|
|`AssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly.|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly (« parent ») à l’origine de la demande.|
|`Success`|`win:Boolean`|Indique si le chargement de l’assembly a réussi.|
|`ResultAssemblyName`|`win:UnicodeString`|Nom de l’assembly qui a été chargé.|
|`ResultAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly qui a été chargé à partir de.|
|`Cached`|`win:UnicodeString`|Indique si la charge a été mise en cache.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="resolutionattempted-event"></a>Événement ResolutionAttempted

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|292|Une charge d’assembly a été demandée.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`Stage`|`win:UInt16`|Étape de résolution.<br/><br/>0 : Rechercher dans le chargement.<br/><br/>1 : contexte de chargement de l’assembly</br><br/>2 : assemblys d’application.<br/><br/>3 : contexte de secours du contexte de chargement de l’assembly par défaut. <br/><br/>4 : résoudre l’assembly satellite. <br/><br/>5 : résolution du contexte de chargement de l’assembly.<br/><br/>6 : résolution d’assembly AppDomain.
|`AssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly.|
|`Result`|`win:UInt16`|Résultat de la tentative de résolution.<br/><br/>0 : réussite<br/><br/>1 : assembly NotFound<br/><br/>2 : version non compatible<br/><br/>3 : nom d’assembly incompatible<br/><br/>4 : échec<br/><br/>5 : exception|
|`ResultAssemblyName`|`win:UnicodeString`|Nom de l’assembly qui a été résolu.|
|`ResultAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly qui a été résolu à partir de.|
|`ErrorMessage`|`win:UnicodeString`|Message d’erreur s’il existe une exception.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a>Événement AssemblyLoadContextResolvingHandlerInvoked

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|293|Un gestionnaire [AssemblyLoadContext. Resolution](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) a été appelé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`HandlerName`|`win:UnicodeString`|Nom du gestionnaire appelé.|
|`AssemblyLoadContext`|`win:UnicodeString`|Contexte de chargement de l’assembly.|
|`ResultAssemblyName`|`win:UnicodeString`|Nom de l’assembly qui a été résolu.|
|`ResultAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly qui a été résolu à partir de.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a>Événement AppDomainAssemblyResolveHandlerInvoked

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|294|Un <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> gestionnaire a été appelé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`HandlerName`|`win:UnicodeString`|Nom du gestionnaire appelé.|
|`ResultAssemblyName`|`win:UnicodeString`|Nom de l’assembly qui a été résolu.|
|`ResultAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly qui a été résolu à partir de.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a>Événement AssemblyLoadFromResolveHandlerInvoked

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|295|Un <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> gestionnaire a été appelé.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Nom de l’assembly.|
|`IsTrackedLoad`|`win:Boolean`|Indique si le chargement de l’assembly est suivi.|
|`RequestingAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly demandeur.|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|Chemin d’accès de l’assembly qui a été demandé.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="knownpathprobed-event"></a>Événement KnownPathProbed

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 0x4|Informatif (4)|

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`KnownPathProbed`|296|Un chemin d’accès connu a été détecté pour un assembly.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|Chemin d’accès détecté.|
|`Source`|`win:UInt16`|Source du chemin d’accès détecté.<br/><br/>0x0 : assemblys de l’application.<br/><br/>0x1 : chemin d’accès à l’image native de l’application.<br/><br/>0X2 : chemin d’accès à l’application.</br><br/>0x3 : racines de ressource de plateforme.<br/><br/>0x4 : sous-répertoire satellite.</br>|
|`Result`|`win:UInt32`|HRESULT pour la sonde.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
