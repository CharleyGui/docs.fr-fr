---
title: Interfaces de débogage
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff589285d81a3febf887bba976b62a9ae4a573c8
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025944"
---
# <a name="debugging-interfaces"></a>Interfaces de débogage
Cette section décrit les interfaces non managées qui gèrent le débogage d'un programme s'exécutant dans le Common Language Runtime (CLR).  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICLRDataEnumMemoryRegions, Interface](iclrdataenummemoryregions-interface.md)\
 Fournit une méthode pour énumérer les régions de mémoire qui sont spécifiées par les appelants.  
  
 [ICLRDataEnumMemoryRegionsCallback, Interface](iclrdataenummemoryregionscallback-interface.md)\
 Fournit une méthode de rappel pour que `EnumMemoryRegions` rapporte au débogueur le résultat d'une tentative d'énumération d'une région spécifiée de mémoire.  
  
 [ICLRDataTarget, Interface](iclrdatatarget-interface.md)\
 Fournit des méthodes pour l'interaction avec un processus CLR cible.  
  
 [ICLRDataTarget2, Interface](iclrdatatarget2-interface.md)\
 Sous-classe de `ICLRDataTarget` qui est utilisée par la couche des services d'accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.  
  
 [Iclrdatatarget3, Interface](iclrdatatarget3-interface.md)\
 Une sous-classe de [ICLRDataTarget2](iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur les exceptions.  
  
 [ICLRDebugging, Interface](iclrdebugging-interface.md)\
 Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.  
  
 [ICLRDebuggingLibraryProvider, Interface](iclrdebugginglibraryprovider-interface.md)\
 Inclut le [ProvideLibrary, méthode](iclrdebugginglibraryprovider-providelibrary-method.md) (méthode), qui obtient un fournisseur de bibliothèque interface de rappel qui permet de common language runtime des bibliothèques de débogage spécifiques à la version être à la demande et le chargement.  
  
 [ICLRMetadataLocator, Interface](iclrmetadatalocator-interface.md)\
 Interface utilisée par la couche des services d'accès aux données pour localiser les métadonnées des assemblys dans un processus cible.  
  
 [ICorDebug, Interface](icordebug-interface.md)\
 Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l'environnement du CLR.  
  
 [ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\
 Fournit des méthodes pour le débogage de domaines d'application.  
  
 [ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\
 Fournit des méthodes destinées au travail avec les tableaux, les pointeurs, les pointeurs fonction et les types ByRef. Cette interface est une extension de l'interface `ICorDebugAppDomain`.  
  
 [Icordebugappdomain3, Interface](icordebugappdomain3-interface.md)\
 Fournit des méthodes pour travailler avec les types Windows Runtime dans un domaine d’application. Cette interface est une extension des interfaces `ICorDebugAppDomain` et `ICorDebugAppDomain2`.  
  
 [Icordebugappdomain4, Interface](icordebugappdomain4-interface.md)\
 Étend logiquement le [ICorDebugAppDomain](icordebugappdomain-interface.md) interface permettant d’obtenir un objet managé à partir d’un wrapper CCW.  
  
 [ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\
 Fournit une méthode qui retourne un nombre spécifié de valeurs `ICorDebugAppDomain` qui démarrent à l'emplacement suivant dans l'énumération.  
  
 [ICorDebugArrayValue (Interface)](icordebugarrayvalue-interface.md)\
 Sous-classe de `ICorDebugHeapValue` qui représente un tableau unidimensionnel ou multidimensionnel.  
  
 [ICorDebugAssembly (Interface)](icordebugassembly-interface.md)\
 Représente un assembly.  
  
 [ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\
 Représente un assembly. Cette interface est une extension de l'interface `ICorDebugAssembly`.  
  
 [ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\
 Étend logiquement le [ICorDebugAssembly](icordebugassembly-interface.md) interface pour fournir la prise en charge pour les assemblys conteneurs et leurs assemblys de relation contenant-contenus. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugAssembly`.  
  
 [ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\
 Fournit un énumérateur pour une liste de [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.  
  
 [ICorDebugBoxValue (Interface)](icordebugboxvalue-interface.md)\
 Sous-classe de `ICorDebugHeapValue` qui représente un objet classe de valeur boxed.  
  
 [ICorDebugBreakpoint (Interface)](icordebugbreakpoint-interface.md)\
 Représente un point d'arrêt dans une fonction ou un point de contrôle sur une valeur.  
  
 [ICorDebugBreakpointEnum (Interface)](icordebugbreakpointenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugBreakpoint`.  
  
 [ICorDebugChain (Interface)](icordebugchain-interface.md)\
 Représente un segment d'une pile des appels physique ou logique.  
  
 [ICorDebugChainEnum (Interface)](icordebugchainenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugChain`.  
  
 [ICorDebugClass (Interface)](icordebugclass-interface.md)\
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugClass` représente le type générique non instancié.  
  
 [ICorDebugClass2 Interface](icordebugclass2-interface.md)\
 Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>. Cette interface étend `ICorDebugClass`.  
  
 [ICorDebugCode (Interface)](icordebugcode-interface1.md)\
 Représente un segment de code MSIL ou de code natif.  
  
 [ICorDebugCode2 Interface](icordebugcode2-interface.md)\
 Fournit des méthodes qui étendent les fonctions de `ICorDebugCode`.  
  
 [Icordebugcode3, Interface](icordebugcode3-interface.md)\
 Fournit une méthode qui étend [ICorDebugCode](icordebugcode-interface1.md) et [ICorDebugCode2](icordebugcode2-interface.md) pour fournir des informations sur une valeur de retour managée.  
  
 [ICorDebugCode4 Interface](icordebugcode4-interface.md)\
 Fournit une méthode qui permet à un débogueur énumérer les variables locales et les arguments dans une fonction.  
  
 [ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugCode`.  
  
 [Interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)\
 Fournit des méthodes pour récupérer des objets d'interface mis en cache.  
  
 [ICorDebugContext (Interface)](icordebugcontext-interface.md)\
 Représente un objet de contexte. Cette interface n'a pas encore été implémentée.  
  
 [ICorDebugController (Interface)](icordebugcontroller-interface.md)\
 Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.  
  
 [ICorDebugDataTarget, Interface](icordebugdatatarget-interface.md)\
 Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.  
  
 [ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\
 Étend logiquement le [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\
 Étend logiquement le [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface pour fournir des informations sur les modules chargés. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugdebugevent, Interface](icordebugdebugevent-interface.md)\
 Définit l’interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEnum (Interface)](icordebugenum-interface1.md)\
 Sert d’interface de base abstraite pour déboguer des énumérateurs.  
  
 [ICorDebugErrorInfoEnum (Interface)](icordebugerrorinfoenum-interface.md)\
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEval (Interface)](icordebugeval-interface.md)\
 Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.  
  
 [ICorDebugEval2 (Interface)](icordebugeval2-interface.md)\
 Étend `ICorDebugEval` pour offrir une prise en charge pour les types génériques.  
  
 [Icordebugexceptiondebugevent, Interface](icordebugexceptiondebugevent-interface.md)\
 Étend la [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface pour prendre en charge les événements d’exception. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\
 Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.  
  
 [Icordebugexceptionobjectvalue, Interface](icordebugexceptionobjectvalue-interface.md)\
 Étend la [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface pour fournir des informations de trace de pile à partir d’un objet d’exception géré.  
  
 [ICorDebugFrame (Interface)](icordebugframe-interface.md)\
 Représente un frame sur la pile en cours.  
  
 [ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugFrame`.  
  
 [ICorDebugFunction (Interface)](icordebugfunction-interface1.md)\
 Représente une fonction ou une méthode managée.  
  
 [ICorDebugFunction2 (Interface)](icordebugfunction2-interface.md)\
 Étend logiquement `ICorDebugFunction` pour prendre en charge le débogage pas à pas pour « Uniquement mon code ».  
  
 [Icordebugfunction3, Interface](icordebugfunction3-interface.md)\
 Étend logiquement le [ICorDebugFunction](icordebugfunction-interface1.md) interface pour fournir l’accès au code à partir d’une demande ReJIT.  
  
 [ICorDebugFunctionBreakpoint (Interface)](icordebugfunctionbreakpoint-interface.md)\
 Étend `ICorDebugBreakpoint` pour prendre en charge les points d'arrêt au sein de fonctions.  
  
 [ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\
 Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.  
  
 [ICorDebugGenericValue (Interface)](icordebuggenericvalue-interface.md)\
 Sous-classe de `ICorDebugValue` qui s'applique à toutes les valeurs. Cette interface fournit les méthodes Get et Set pour la valeur.  
  
 [ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\
 Fournit un énumérateur pour un objet qui mappe les GUID et leurs objets `ICorDebugType` correspondants.  
  
 [ICorDebugHandleValue (Interface)](icordebughandlevalue-interface.md)\
 Sous-classe de `ICorDebugReferenceValue` qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.  
  
 [ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\
 Fournit un énumérateur pour les objets sur le tas managé.  
  
 [ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\
 Fournit un énumérateur pour les régions de mémoire du tas managé.  
  
 [ICorDebugHeapValue (Interface)](icordebugheapvalue-interface.md)\
 Sous-classe de `ICorDebugValue` qui représente un objet qui a été collecté par le garbage collector du CLR.  
  
 [ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\
 Extension de `ICorDebugHeapValue` qui fournit la prise en charge des handles d’exécution.  
  
 [ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\
 Expose les propriétés du verrou du moniteur d'objets.  
  
 [Icordebugilcode, Interface](icordebugilcode-interface.md)\
 Représente un segment du code en langage intermédiaire.  
  
 [Icordebugilcode2, Interface](icordebugilcode2-interface.md)\
 Étend logiquement le [ICorDebugILCode](icordebugilcode-interface.md) interface pour fournir des méthodes qui retournent le jeton de signature de variable locale d’une fonction, et qui correspondent le langage intermédiaire instrumenté (IL) d’un profileur aux offsets intermédiaire de la méthode d’origine décalages.  
  
 [ICorDebugILFrame (Interface)](icordebugilframe-interface.md)\
 Représente un frame de pile de code MSIL.  
  
 [ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\
 Extension logique de `ICorDebugILFrame`.  
  
 [Icordebugilframe3, Interface](icordebugilframe3-interface.md)\
 Fournit une méthode qui encapsule la valeur de retour d'une fonction.  
  
 [ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\
 Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire. Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
 [Icordebuginstancefieldsymbol, Interface](icordebuginstancefieldsymbol-interface.md)\
 Représente les informations sur les symboles de débogage pour un champ d’instance. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\
 Identifie les types de frame pour le débogueur.  
  
 [ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\
 Fournit des informations sur les frames internes, notamment l’adresse de la pile et la position par rapport à [ICorDebugFrame](icordebugframe-interface.md) objets.  
  
 [ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\
 Fournit des informations sur un module chargé. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugManagedCallback, Interface](icordebugmanagedcallback-interface.md)\
 Fournit des méthodes pour traiter les rappels de débogueur.  
  
 [ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\
 Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur. `ICorDebugManagedCallback2` est une extension logique de `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\
 Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.  
  
 [ICorDebugMDA Interface](icordebugmda-interface.md)\
 Représente un message d'Assistant Débogage managé (MDA).  
  
 [Icordebugmemorybuffer, Interface](icordebugmemorybuffer-interface.md)\
 Représente une mémoire tampon en mémoire. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\
 Fournit des informations sur un assembly fusionné. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugMetaDataLocator, Interface](icordebugmetadatalocator-interface.md)\
 Fournit des informations de métadonnées au débogueur.  
  
 [ICorDebugModule Interface](icordebugmodule-interface.md)\
 Représente un module CLR qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).  
  
 [ICorDebugModule2 Interface](icordebugmodule2-interface.md)\
 Sert d’extension logique de `ICorDebugModule`.  
  
 [ICorDebugModule3 Interface](icordebugmodule3-interface.md)\
 Crée un lecteur de symboles pour un module dynamique.  
  
 [ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux modules spécifiques.  
  
 [ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\
 Étend la [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface pour prendre en charge les événements au niveau du module. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugModule`.  
  
 [ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\
 Étend la [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface pour prendre en charge des cibles de données mutables.  
  
 [ICorDebugNativeFrame (Interface)](icordebugnativeframe-interface.md)\
 Implémentation spécialisée de `ICorDebugFrame` utilisée pour les frames natifs.  
  
 [ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\
 Fournit des méthodes qui testent les relations entre frames enfant et parent.  
  
 [ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux d'objets par leurs adresses virtuelles relatives.  
  
 [ICorDebugObjectValue (Interface)](icordebugobjectvalue-interface.md)\
 Sous-classe de `ICorDebugValue` qui représente une valeur contenant un objet.  
  
 [ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\
 Étend `ICorDebugObjectValue` pour prendre en charge l'héritage et les substitutions.  
  
 [ICorDebugProcess (Interface)](icordebugprocess-interface.md)\
 Représente un processus qui exécute le code managé.  
  
 [ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\
 Extension logique de `ICorDebugProcess`.  
  
 [ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\
 Contrôle les notifications de débogueur personnalisées.

 [ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\
 Prend en charge hors de contrôle de l’exécution de processus.
  
 [ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\
 Étend la [ICorDebugProcess](icordebugprocess-interface.md) local de l’interface pour prendre en charge d’accès pour le tas managé, pour fournir des informations sur le garbage collection d’objets gérés et pour déterminer si un débogueur charge des images à partir de l’application cache des images natives.  
  
 [ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\
 Étend logiquement le [ICorDebugProcess](icordebugprocess-interface.md) interface pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont encodés dans les événements de débogage d’exception native et fractionnement de module virtuel. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\
 Fournit une méthode qui configure le débogueur afin de gérer les mises à jour de métadonnées en mémoire dans le processus cible.  
  
 [ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\
 Étend logiquement le [ICorDebugProcess](icordebugprocess-interface.md) interface pour activer ou désactiver certains types de [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) rappels d’exception.  
  
 [ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugProcess`.  
  
 [ICorDebugReferenceValue (Interface)](icordebugreferencevalue-interface.md)\
 Sous-classe de `ICorDebugValue` qui prend en charge les types référence.  
  
 [ICorDebugRegisterSet, Interface](icordebugregisterset-interface.md)\
 Représente le jeu de registres disponible sur l'ordinateur qui exécute actuellement le code.  
  
 [ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\
 Étend les fonctionnalités de `ICorDebugRegisterSet` pour les plateformes matérielles qui possèdent plus de 64 registres.  
  
 [Icordebugremote, Interface](icordebugremote-interface.md)\
 Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.  
  
 [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\
 Fournit des méthodes qui vous permettent de déboguer les applications Silverlight dans l'environnement du CLR.  
  
 [ICorDebugRuntimeUnwindableFrame, Interface](icordebugruntimeunwindableframe-interface.md)\
 Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.  
  
 [ICorDebugStackWalk, Interface](icordebugstackwalk-interface.md)\
 Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.  
  
 [Icordebugstaticfieldsymbol, Interface](icordebugstaticfieldsymbol-interface.md)\
 Représente les informations sur les symboles de débogage pour un champ static. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugStepper (Interface)](icordebugstepper-interface.md)\
 Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.  
  
 [ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\
 Prend en charge le débogage « Uniquement mon code ».  
  
 [ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugStepper`.  
  
 [ICorDebugStringValue (Interface)](icordebugstringvalue-interface.md)\
 Sous-classe de `ICorDebugHeapValue` qui s'applique aux valeurs de chaîne.  
  
 [ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\
 Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\
 Étend logiquement le [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface pour récupérer des informations symboliques de débogage supplémentaires. **Disponible sur .NET Native uniquement.**  
  
 [ICorDebugThread (Interface)](icordebugthread-interface.md)\
 Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
 [ICorDebugThread2 Interface](icordebugthread2-interface.md)\
 Sert d’extension logique de `ICorDebugThread`.  
  
 [ICorDebugThread3 Interface](icordebugthread3-interface.md)\
 Fournit le point d’entrée pour le [ICorDebugStackWalk](icordebugstackwalk-interface.md) et les interfaces correspondantes.  
  
 [ICorDebugThread4 Interface](icordebugthread4-interface.md)\
 Fournit des informations sur le blocage des threads.  
  
 [ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugThread`.  
  
 [ICorDebugType (Interface)](icordebugtype-interface.md)\
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugType` représente le type générique instancié.  
  
 [Icordebugtype2, Interface](icordebugtype2-interface.md)\
 Étend la [ICorDebugType](icordebugtype-interface.md) interface pour récupérer l’identificateur de type d’un type de base ou complexe (défini par l’utilisateur).  
  
 [ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugType`.  
  
 [ICorDebugUnmanagedCallback, Interface](icordebugunmanagedcallback-interface.md)\
 Fournit une notification des événements natifs qui ne sont pas mis directement en rapport avec le CLR.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Représente une valeur de lecture ou d'écriture dans le processus en cours de débogage.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Étend `ICorDebugValue` pour prendre en charge `ICorDebugType`.  
  
 [ICorDebugValue3 Interface](icordebugvalue3-interface.md)\
 Étend les interfaces de « ICorDebugValue » et « ICorDebugValue2 » pour prendre en charge pour les tableaux qui sont supérieures à 2 Go.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux valeurs spécifiques.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugValue`.  
  
 [ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\
 Représente une variable locale ou un argument d’une fonction.  
  
 [ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\
 Fournit un énumérateur pour les variables locales et les arguments dans une fonction.  
  
 [ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\
 Récupère les informations sur les symboles de débogage pour une variable. **Disponible sur .NET Native uniquement.**  
  
 [Icordebugvirtualunwinder, Interface](icordebugvirtualunwinder-interface.md)\
 Fournit des méthodes pour faciliter le déroulement de la pile. **Disponible sur .NET Native uniquement.**  
  
 [ICorPublish, Interface](icorpublish-interface.md)\
 Sert d'interface générale pour les processus de publication.  
  
 [ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\
 Représente et fournit des informations à propos d'un domaine d'application.  
  
 [ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\
 Fournit des méthodes qui parcourent une collection d’objets `ICorPublishAppDomain` qui existent actuellement dans un processus.  
  
 [ICorPublishEnum, Interface](icorpublishenum-interface.md)\
 Sert comme base abstraite pour la publication des énumérateurs.  
  
 [ICorPublishProcess, Interface](icorpublishprocess-interface.md)\
 Fournit des méthodes qui permettent d'accéder aux informations sur un processus.  
  
 [ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\
 Fournit des méthodes qui parcourent une collection d’objets `ICorPublishProcess`.  

 [Interface de ISOSDacInterface](isosdacinterface-interface.md)\
 Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS`.

 [Interface de IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)\
 Fournit des méthodes pour obtenir des informations sur une définition de méthode.
 
 [Interface de IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\
 Fournit des méthodes pour obtenir des informations sur une instance de méthode.
 
 [Interface de IXCLRDataModule](ixclrdatamodule-interface.md)\
 Fournit des méthodes pour obtenir des informations sur un module chargé.
 
 [Interface de IXCLRDataProcess](ixclrdataprocess-interface.md)\
 Fournit des méthodes pour obtenir des informations relatives à un processus.
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses de débogage](debugging-coclasses.md)\
 [Fonctions statiques globales de débogage](debugging-global-static-functions.md)\
 [Énumérations de débogage](debugging-enumerations.md)\
 [Structures de débogage](debugging-structures.md)\
