---
title: Interfaces de débogage
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097197"
---
# <a name="debugging-interfaces"></a>Interfaces de débogage
Cette section décrit les interfaces non managées qui gèrent le débogage d'un programme s'exécutant dans le Common Language Runtime (CLR).  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICLRDataEnumMemoryRegions, Interface](iclrdataenummemoryregions-interface.md)\
 Fournit une méthode pour énumérer les régions de mémoire qui sont spécifiées par les appelants.  
  
 \ de l' [interface ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)
 Fournit une méthode de rappel pour que `EnumMemoryRegions` rapporte au débogueur le résultat d'une tentative d'énumération d'une région spécifiée de mémoire.  
  
 [ICLRDataTarget, Interface](iclrdatatarget-interface.md)\
 Fournit des méthodes pour l'interaction avec un processus CLR cible.  
  
 \ de l' [interface ICLRDataTarget2](iclrdatatarget2-interface.md)
 Sous-classe de `ICLRDataTarget` qui est utilisée par la couche des services d'accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.  
  
 \ de l' [interface ICLRDataTarget3](iclrdatatarget3-interface.md)
 Sous-classe de [ICLRDataTarget2](iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur les exceptions.  
  
 \ de l' [interface ICLRDebugging](iclrdebugging-interface.md)
 Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.  
  
 \ de l' [interface ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)
 Comprend la méthode de [méthode ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.  
  
 \ de l' [interface ICLRMetadataLocator](iclrmetadatalocator-interface.md)
 Interface utilisée par la couche des services d'accès aux données pour localiser les métadonnées des assemblys dans un processus cible.  
  
 \ de l' [interface ICorDebug](icordebug-interface.md)
 Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l'environnement du CLR.  
  
 \ de l' [interface ICorDebugAppDomain](icordebugappdomain-interface.md)
 Fournit des méthodes pour le débogage de domaines d'application.  
  
 \ de l' [interface ICorDebugAppDomain2](icordebugappdomain2-interface.md)
 Fournit des méthodes destinées au travail avec les tableaux, les pointeurs, les pointeurs fonction et les types ByRef. Cette interface est une extension de l'interface `ICorDebugAppDomain`.  
  
 \ de l' [interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)
 Fournit des méthodes pour utiliser les types de Windows Runtime dans un domaine d’application. Cette interface est une extension des interfaces `ICorDebugAppDomain` et `ICorDebugAppDomain2`.  
  
 \ de l' [interface icordebugappdomain4,](icordebugappdomain4-interface.md)
 Étend logiquement l’interface [ICorDebugAppDomain](icordebugappdomain-interface.md) pour obtenir un objet managé à partir d’un wrapper CCW (COM Callable Wrapper).  
  
 \ de l' [interface ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)
 Fournit une méthode qui retourne un nombre spécifié de valeurs `ICorDebugAppDomain` qui démarrent à l'emplacement suivant dans l'énumération.  
  
 [Interface ICorDebugArrayValue](icordebugarrayvalue-interface.md)\
 Sous-classe de `ICorDebugHeapValue` qui représente un tableau unidimensionnel ou multidimensionnel.  
  
 \ de l' [interface ICorDebugAssembly](icordebugassembly-interface.md)
 Représente un assembly.  
  
 \ de l' [interface ICorDebugAssembly2](icordebugassembly2-interface.md)
 Représente un assembly. Cette interface est une extension de l'interface `ICorDebugAssembly`.  
  
 \ de l' [interface méthode icordebugassembly3](icordebugassembly3-interface.md)
 Étend logiquement l’interface [ICorDebugAssembly](icordebugassembly-interface.md) pour assurer la prise en charge des assemblys de conteneur et de leurs assemblys contenus. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugAssembly`.  
  
 \ de l' [interface ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)
 Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
 \ de l' [interface ICorDebugBoxValue](icordebugboxvalue-interface.md)
 Sous-classe de `ICorDebugHeapValue` qui représente un objet classe de valeur boxed.  
  
 [Interface ICorDebugBreakpoint](icordebugbreakpoint-interface.md)\
 Représente un point d'arrêt dans une fonction ou un point de contrôle sur une valeur.  
  
 \ de l' [interface ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugBreakpoint`.  
  
 [ICorDebugChain, Interface](icordebugchain-interface.md)\
 Représente un segment d'une pile des appels physique ou logique.  
  
 \ de l' [interface ICorDebugChainEnum](icordebugchainenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugChain`.  
  
 [ICorDebugClass, Interface](icordebugclass-interface.md)\
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugClass` représente le type générique non instancié.  
  
 \ de l' [interface ICorDebugClass2](icordebugclass2-interface.md)
 Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>. Cette interface étend `ICorDebugClass`.  
  
 \ de l' [interface ICorDebugCode](icordebugcode-interface1.md)
 Représente un segment de code MSIL ou de code natif.  
  
 \ de l' [interface ICorDebugCode2](icordebugcode2-interface.md)
 Fournit des méthodes qui étendent les fonctions de `ICorDebugCode`.  
  
 \ de l' [interface ICorDebugCode3](icordebugcode3-interface.md)
 Fournit une méthode qui étend [ICorDebugCode](icordebugcode-interface1.md) et [ICorDebugCode2](icordebugcode2-interface.md) pour fournir des informations sur une valeur de retour managée.  
  
 \ de l' [interface ICorDebugCode4](icordebugcode4-interface.md)
 Fournit une méthode qui permet à un débogueur d’énumérer les variables et les arguments locaux dans une fonction.  
  
 \ de l' [interface ICorDebugCodeEnum](icordebugcodeenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugCode`.  
  
 \ de l' [interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)
 Fournit des méthodes pour récupérer des objets d'interface mis en cache.  
  
 \ de l' [interface ICorDebugContext](icordebugcontext-interface.md)
 Représente un objet de contexte. Cette interface n'a pas encore été implémentée.  
  
 \ de l' [interface ICorDebugController](icordebugcontroller-interface.md)
 Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.  
  
 [ICorDebugDataTarget, Interface](icordebugdatatarget-interface.md)\
 Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.  
  
 \ de l' [interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
 Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) . **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface icordebugdatatarget3,](icordebugdatatarget3-interface.md)
 Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)
 Définit l’interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)
 Obsolète. N'utilisez pas cette interface.  
  
 \ de l' [interface ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEnum, Interface](icordebugenum-interface1.md)\
 Sert d’interface de base abstraite pour déboguer des énumérateurs.  
  
 \ de l' [interface ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)
 Obsolète. N'utilisez pas cette interface.  
  
 [ICorDebugEval, Interface](icordebugeval-interface.md)\
 Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.  
  
 \ de l' [interface ICorDebugEval2](icordebugeval2-interface.md)
 Étend `ICorDebugEval` pour offrir une prise en charge pour les types génériques.  
  
 \ de l' [interface icordebugexceptiondebugevent,](icordebugexceptiondebugevent-interface.md)
 Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements d’exception. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md)
 Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.  
  
 \ de l' [interface icordebugexceptionobjectvalue,](icordebugexceptionobjectvalue-interface.md)
 Étend l’interface [ICorDebugObjectValue](icordebugobjectvalue-interface.md) pour fournir des informations de trace de la pile à partir d’un objet exception managée.  
  
 [Interface ICorDebugFrame](icordebugframe-interface.md)\
 Représente un frame sur la pile en cours.  
  
 \ de l' [interface ICorDebugFrameEnum](icordebugframeenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugFrame`.  
  
 \ de l' [interface ICorDebugFunction](icordebugfunction-interface1.md)
 Représente une fonction ou une méthode managée.  
  
 [ICorDebugFunction2, Interface](icordebugfunction2-interface.md)\
 Étend logiquement `ICorDebugFunction` pour prendre en charge le débogage pas à pas pour « Uniquement mon code ».  
  
 \ de l' [interface icordebugfunction3,](icordebugfunction3-interface.md)
 Étend logiquement l’interface [ICorDebugFunction](icordebugfunction-interface1.md) pour fournir l’accès au code à partir d’une demande ReJIT.  
  
 [Interface ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)\
 Étend `ICorDebugBreakpoint` pour prendre en charge les points d'arrêt au sein de fonctions.  
  
 \ de l' [interface icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md)
 Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.  
  
 \ de l' [interface ICorDebugGenericValue](icordebuggenericvalue-interface.md)
 Sous-classe de `ICorDebugValue` qui s'applique à toutes les valeurs. Cette interface fournit les méthodes Get et Set pour la valeur.  
  
 \ de l' [interface icordebugguidtotypeenum,](icordebugguidtotypeenum-interface.md)
 Fournit un énumérateur pour un objet qui mappe les GUID et leurs objets `ICorDebugType` correspondants.  
  
 \ de l' [interface ICorDebugHandleValue](icordebughandlevalue-interface.md)
 Sous-classe de `ICorDebugReferenceValue` qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.  
  
 \ de l' [interface icordebugheapenum,](icordebugheapenum-interface.md)
 Fournit un énumérateur pour les objets sur le tas managé.  
  
 \ de l' [interface icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md)
 Fournit un énumérateur pour les régions de mémoire du tas managé.  
  
 \ de l' [interface ICorDebugHeapValue](icordebugheapvalue-interface.md)
 Sous-classe de `ICorDebugValue` qui représente un objet qui a été collecté par le garbage collector du CLR.  
  
 \ de l' [interface ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)
 Extension de `ICorDebugHeapValue` qui fournit la prise en charge des handles d’exécution.  
  
 \ de l' [interface ICorDebugHeapValue3](icordebugheapvalue3-interface.md)
 Expose les propriétés du verrou du moniteur d'objets.  
  
 \ de l' [interface ICorDebugILCode](icordebugilcode-interface.md)
 Représente un segment du code en langage intermédiaire.  
  
 \ de l' [interface ICorDebugILCode2](icordebugilcode2-interface.md)
 Étend logiquement l’interface [ICorDebugILCode](icordebugilcode-interface.md) pour fournir des méthodes qui retournent le jeton pour la signature de variable locale d’une fonction et qui mappent les offsets du langage intermédiaire instrumenté d’un profileur aux DÉCALAGEs il de la méthode d’origine.  
  
 \ d' [interface ICorDebugILFrame](icordebugilframe-interface.md)
 Représente un frame de pile de code MSIL.  
  
 \ de l' [interface ICorDebugILFrame2](icordebugilframe2-interface.md)
 Extension logique de `ICorDebugILFrame`.  
  
 \ de l' [interface ICorDebugILFrame3](icordebugilframe3-interface.md)
 Fournit une méthode qui encapsule la valeur de retour d'une fonction.  
  
 \ de l' [interface ICorDebugILFrame4](icordebugilframe4-interface.md)
 Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire. Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
 \ de l' [interface icordebuginstancefieldsymbol,](icordebuginstancefieldsymbol-interface.md)
 Représente les informations sur les symboles de débogage pour un champ d’instance. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugInternalFrame](icordebuginternalframe-interface.md)
 Identifie les types de frame pour le débogueur.  
  
 \ de l' [interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
 Fournit des informations sur les frames internes, y compris l’adresse et la position de la pile par rapport aux objets [ICorDebugFrame](icordebugframe-interface.md) .  
  
 \ de l' [interface ICorDebugLoadedModule](icordebugloadedmodule-interface.md)
 Fournit des informations sur un module chargé. **Disponible uniquement sur .NET Native.**  
  
 [ICorDebugManagedCallback, Interface](icordebugmanagedcallback-interface.md)\
 Fournit des méthodes pour traiter les rappels de débogueur.  
  
 \ de l' [interface ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)
 Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur. `ICorDebugManagedCallback2` est une extension logique de `ICorDebugManagedCallback`.  
  
 \ de l' [interface ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)
 Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.  
  
 [ICorDebugMDA, Interface](icordebugmda-interface.md)\
 Représente un message d'Assistant Débogage managé (MDA).  
  
 \ de l' [interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
 Représente une mémoire tampon en mémoire. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
 Fournit des informations sur un assembly fusionné. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)
 Fournit des informations de métadonnées au débogueur.  
  
 \ de l' [interface ICorDebugModule](icordebugmodule-interface.md)
 Représente un module CLR qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).  
  
 \ de l' [interface ICorDebugModule2](icordebugmodule2-interface.md)
 Sert d’extension logique de `ICorDebugModule`.  
  
 \ de l' [interface ICorDebugModule3](icordebugmodule3-interface.md)
 Crée un lecteur de symboles pour un module dynamique.  
  
 \ de l' [interface ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux modules spécifiques.  
  
 \ de l' [interface icordebugmoduledebugevent,](icordebugmoduledebugevent-interface.md)
 Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements au niveau du module. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugModuleEnum](icordebugmoduleenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugModule`.  
  
 \ de l' [interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
 Étend l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour prendre en charge les cibles de données mutables.  
  
 [ICorDebugNativeFrame, Interface](icordebugnativeframe-interface.md)\
 Implémentation spécialisée de `ICorDebugFrame` utilisée pour les frames natifs.  
  
 \ de l' [interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
 Fournit des méthodes qui testent les relations entre frames enfant et parent.  
  
 \ de l' [interface ICorDebugObjectEnum](icordebugobjectenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux d'objets par leurs adresses virtuelles relatives.  
  
 \ de l' [interface ICorDebugObjectValue](icordebugobjectvalue-interface.md)
 Sous-classe de `ICorDebugValue` qui représente une valeur contenant un objet.  
  
 \ de l' [interface ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)
 Étend `ICorDebugObjectValue` pour prendre en charge l'héritage et les substitutions.  
  
 \ de l' [interface ICorDebugProcess](icordebugprocess-interface.md)
 Représente un processus qui exécute le code managé.  
  
 \ de l' [interface ICorDebugProcess2](icordebugprocess2-interface1.md)
 Extension logique de `ICorDebugProcess`.  
  
 \ de l' [interface ICorDebugProcess3](icordebugprocess3-interface.md)
 Contrôle les notifications de débogueur personnalisées.

 \ de l' [interface ICorDebugProcess4](icordebugprocess4-interface.md)
 Prend en charge le contrôle de l’exécution hors processus.
  
 \ de l' [interface ICorDebugProcess5](icordebugprocess5-interface.md)
 Étend l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour prendre en charge l’accès au tas managé, pour fournir des informations sur garbage collection d’objets managés et pour déterminer si un débogueur charge des images à partir du cache des images natives locales de l’application.  
  
 \ de l' [interface ICorDebugProcess6](icordebugprocess6-interface.md)
 Étend logiquement l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont encodés dans des événements de débogage d’exception native et le fractionnement de module virtuel. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface icordebugprocess7,](icordebugprocess7-interface.md)
 Fournit une méthode qui configure le débogueur afin de gérer les mises à jour de métadonnées en mémoire dans le processus cible.  
  
 \ de l' [interface icordebugprocess8,](icordebugprocess8-interface.md)
 Étend logiquement l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour activer ou désactiver certains types de rappels d’exception [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
 \ de l' [interface ICorDebugProcessEnum](icordebugprocessenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugProcess`.  
  
 [ICorDebugReferenceValue, Interface](icordebugreferencevalue-interface.md)\
 Sous-classe de `ICorDebugValue` qui prend en charge les types référence.  
  
 \ de l' [interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
 Représente le jeu de registres disponible sur l'ordinateur qui exécute actuellement le code.  
  
 \ de l' [interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
 Étend les fonctionnalités de `ICorDebugRegisterSet` pour les plateformes matérielles qui possèdent plus de 64 registres.  
  
 \ de l' [interface ICorDebugRemote](icordebugremote-interface.md)
 Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.  
  
 \ de l' [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
 Fournit des méthodes qui vous permettent de déboguer les applications Silverlight dans l'environnement du CLR.  
  
 \ de l' [interface ICorDebugRuntimeUnwindableFrame,](icordebugruntimeunwindableframe-interface.md)
 Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.  
  
 \ de l' [interface ICorDebugStackWalk](icordebugstackwalk-interface.md)
 Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.  
  
 \ de l' [interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
 Représente les informations sur les symboles de débogage pour un champ static. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugStepper](icordebugstepper-interface.md)
 Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.  
  
 \ de l' [interface ICorDebugStepper2](icordebugstepper2-interface1.md)
 Prend en charge le débogage « Uniquement mon code ».  
  
 \ de l' [interface ICorDebugStepperEnum](icordebugstepperenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugStepper`.  
  
 [Interface ICorDebugStringValue](icordebugstringvalue-interface.md)\
 Sous-classe de `ICorDebugHeapValue` qui s'applique aux valeurs de chaîne.  
  
 \ de l' [interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
 Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface icordebugsymbolprovider2,](icordebugsymbolprovider2-interface.md)
 Étend logiquement l’interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) pour récupérer des informations supplémentaires sur les symboles de débogage. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugThread](icordebugthread-interface.md)
 Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
 \ de l' [interface ICorDebugThread2](icordebugthread2-interface.md)
 Sert d’extension logique de `ICorDebugThread`.  
  
 \ de l' [interface ICorDebugThread3](icordebugthread3-interface.md)
 Fournit le point d’entrée pour [ICorDebugStackWalk](icordebugstackwalk-interface.md) et les interfaces correspondantes.  
  
 \ de l' [interface ICorDebugThread4](icordebugthread4-interface.md)
 Fournit des informations sur le blocage des threads.  
  
 \ de l' [interface ICorDebugThreadEnum](icordebugthreadenum-interface1.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugThread`.  
  
 [ICorDebugType, Interface](icordebugtype-interface.md)\
 Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugType` représente le type générique instancié.  
  
 \ de l' [interface méthode icordebugtype2](icordebugtype2-interface.md)
 Étend l’interface [ICorDebugType](icordebugtype-interface.md) pour récupérer l’identificateur de type d’un type de base ou un type complexe (défini par l’utilisateur).  
  
 \ de l' [interface ICorDebugTypeEnum](icordebugtypeenum-interface.md)
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugType`.  
  
 \ de l' [interface ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)
 Fournit une notification des événements natifs qui ne sont pas mis directement en rapport avec le CLR.  
  
 \ [ICorDebugValue](icordebugvalue-interface.md)
 Représente une valeur de lecture ou d'écriture dans le processus en cours de débogage.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Étend `ICorDebugValue` pour prendre en charge `ICorDebugType`.  
  
 \ de l' [interface icordebugvalue3,](icordebugvalue3-interface.md)
 Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour assurer la prise en charge des tableaux d’une taille supérieure à 2 Go.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Étend `ICorDebugBreakpoint` pour fournir l'accès aux valeurs spécifiques.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugValue`.  
  
 \ de l' [interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
 Représente une variable locale ou un argument d’une fonction.  
  
 \ de l' [interface ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)
 Fournit un énumérateur aux variables locales et aux arguments dans une fonction.  
  
 \ de l' [interface méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md)
 Récupère les informations sur les symboles de débogage pour une variable. **Disponible uniquement sur .NET Native.**  
  
 \ de l' [interface ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)
 Fournit des méthodes pour faciliter le déroulement de la pile. **Disponible uniquement sur .NET Native.**  
  
 [ICorPublish, Interface](icorpublish-interface.md)\
 Sert d'interface générale pour les processus de publication.  
  
 \ de l' [interface ICorPublishAppDomain](icorpublishappdomain-interface.md)
 Représente et fournit des informations à propos d'un domaine d'application.  
  
 \ de l' [interface ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)
 Fournit des méthodes qui parcourent une collection d’objets `ICorPublishAppDomain` qui existent actuellement dans un processus.  
  
 [Interface ICorPublishEnum](icorpublishenum-interface.md)\
 Sert comme base abstraite pour la publication des énumérateurs.  
  
 [ICorPublishProcess, Interface](icorpublishprocess-interface.md)\
 Fournit des méthodes qui permettent d'accéder aux informations sur un processus.  
  
 \ de l' [interface ICorPublishProcessEnum](icorpublishprocessenum-interface.md)
 Fournit des méthodes qui parcourent une collection d’objets `ICorPublishProcess`.  

 \ de l' [interface ISOSDacInterface](isosdacinterface-interface.md)
 Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS`.

 \ de l' [interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
 Fournit des méthodes pour interroger des informations sur une définition de méthode.
 
 \ de l' [interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
 Fournit des méthodes pour interroger les informations relatives à une instance de méthode.
 
 \ de l' [interface IXCLRDataModule](ixclrdatamodule-interface.md)
 Fournit des méthodes pour interroger des informations sur un module chargé.
 
 \ de l' [interface IXCLRDataProcess](ixclrdataprocess-interface.md)
 Fournit des méthodes pour interroger les informations relatives à un processus.
  
## <a name="related-sections"></a>Rubriques connexes  
 [Débogage des coclasses](debugging-coclasses.md)\
 [Fonctions statiques globales de débogage](debugging-global-static-functions.md)\
 [Énumérations de débogage](debugging-enumerations.md)\
 [Structures de débogage](debugging-structures.md)\
