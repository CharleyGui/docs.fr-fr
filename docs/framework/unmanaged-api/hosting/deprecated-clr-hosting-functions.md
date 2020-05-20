---
title: Fonction d'hébergement du CLR déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 8925278bdf4d48efc9e589ffc4e181d904444e6b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616422"
---
# <a name="deprecated-clr-hosting-functions"></a>Fonction d'hébergement du CLR déconseillées
Cette section décrit les fonctions statiques globales non managées utilisées par les versions antérieures de l’API d’hébergement.  
  
 À l’exception des fonctions d’infrastructure ( `_Cor*` fonctions), qui sont utilisées uniquement par le .NET Framework, ces fonctions ont été dépréciées dans le .NET Framework 4.  
  
## <a name="activation-functions"></a>Fonctions d’activation  
 [ClrCreateManagedInstance, fonction](clrcreatemanagedinstance-function.md)  
 Action déconseillée. Crée une instance du type managé spécifié.  
  
 [CoInitializeCor, fonction](coinitializecor-function.md)  
 Obsolète. Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE, fonction](coinitializeee-function.md)  
 Action déconseillée. Garantit que le moteur d’exécution du CLR est chargé dans un processus. Utilisez à la place la méthode [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) .  
  
 [CorBindToCurrentRuntime, fonction](corbindtocurrentruntime-function.md)  
 Action déconseillée. Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.  
  
 [CorBindToRuntime, fonction](corbindtoruntime-function.md)  
 Action déconseillée. Permet aux hôtes non managés de charger le CLR dans un processus.  
  
 [CorBindToRuntimeByCfg, fonction](corbindtoruntimebycfg-function.md)  
 Action déconseillée. Charge le CLR dans un processus à l’aide des informations de version lues à partir d’un fichier XML.  
  
 [CorBindToRuntimeEx, fonction](corbindtoruntimeex-function.md)  
 Action déconseillée. Permet aux hôtes non managés de charger le CLR dans un processus, et vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
 [CorBindToRuntimeHost, fonction](corbindtoruntimehost-function.md)  
 Action déconseillée. Permet aux hôtes de charger une version spécifiée du CLR dans un processus.  
  
 [GetCORRequiredVersion, fonction](getcorrequiredversion-function.md)  
 Action déconseillée. Obtient le numéro de version CLR requis.  
  
 [GetCORSystemDirectory, fonction](getcorsystemdirectory-function.md)  
 Action déconseillée. Retourne le répertoire d’installation du CLR qui est chargé dans le processus.  
  
 [GetRealProcAddress, fonction](getrealprocaddress-function.md)  
 Action déconseillée. Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.  
  
 [GetRequestedRuntimeInfo, fonction](getrequestedruntimeinfo-function.md)  
 Action déconseillée. Obtient les informations de version et de répertoire relatives au CLR demandé par une application.  
  
## <a name="clr-version-functions"></a>Fonctions de version du CLR  
 Les fonctions de cette section retournent une version CLR ; ils n’activent pas le CLR.  
  
 [GetCORVersion, fonction](getcorversion-function.md)  
 Action déconseillée. Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.  
  
 [GetFileVersion, fonction](getfileversion-function.md)  
 Action déconseillée. Obtient les informations de version du CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.  
  
 [GetRequestedRuntimeVersion, fonction](getrequestedruntimeversion-function.md)  
 Action déconseillée. Obtient le numéro de version du CLR demandé par l’application spécifiée. Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.  
  
 [GetRequestedRuntimeVersionForCLSID, fonction](getrequestedruntimeversionforclsid-function.md)  
 Action déconseillée. Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.  
  
 [GetVersionFromProcess, fonction](getversionfromprocess-function.md)  
 Action déconseillée. Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.  
  
 [LockClrVersion, fonction](lockclrversion-function.md)  
 Action déconseillée. Permet à l’hôte de déterminer la version du CLR qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.  
  
## <a name="hosting-functions"></a>Fonctions d’hébergement  
 [CallFunctionShim, fonction](callfunctionshim-function.md)  
 Action déconseillée. Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.  
  
 [CoEEShutDownCOM, fonction](coeeshutdowncom-function.md)  
 Action déconseillée. Décharge un assembly COM du processus.  
  
 [CorExitProcess, fonction](corexitprocess-function.md)  
 Action déconseillée. Arrête le processus non managé actuel.  
  
 [CorLaunchApplication, fonction](corlaunchapplication-function.md)  
 Action déconseillée. Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.  
  
 [CorMarkThreadInThreadPool, fonction](cormarkthreadinthreadpool-function.md)  
 Action déconseillée. Marque le thread du pool de threads en cours d’exécution pour l’exécution du code managé. À partir de la version 2,0 de .NET Framework, cette fonction n’a aucun effet. Elle n’est pas obligatoire et peut être supprimée de votre code.  
  
 [CoUninitializeCor, fonction](couninitializecor-function.md)  
 Obsolète. Le CLR ne peut pas être déchargé d’un processus.  
  
 [CoUninitializeEE, fonction](couninitializeee-function.md)  
 Obsolète.  
  
 [CreateDebuggingInterfaceFromVersion, fonction](createdebugginginterfacefromversion-function.md)  
 Action déconseillée. Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.  
  
 [CreateICeeFileGen, fonction](createiceefilegen-function.md)  
 Action déconseillée. Crée un objet [ICeeFileGen](iceefilegen-class.md) .  
  
 [DestroyICeeFileGen, fonction](destroyiceefilegen-function.md)  
 Action déconseillée. Détruit un objet [ICeeFileGen](iceefilegen-class.md) .  
  
 [FExecuteInAppDomainCallback (pointeur fonction)](fexecuteinappdomaincallback-function-pointer.md)  
 Action déconseillée. Pointe vers une fonction que le CLR appelle pour exécuter du code managé.  
  
 [FLockClrVersionCallback (pointeur fonction)](flockclrversioncallback-function-pointer.md)  
 Action déconseillée. Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou est terminée.  
  
 [GetCLRIdentityManager, fonction](getclridentitymanager-function.md)  
 Action déconseillée. Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.  
  
 [LoadLibraryShim, fonction](loadlibraryshim-function.md)  
 Action déconseillée. Charge une version spécifiée d’un .NET Framework DLL.  
  
 [LoadStringRC, fonction](loadstringrc-function.md)  
 Action déconseillée. Convertit une valeur HRESULT en message d’erreur à l’aide de la culture par défaut du thread actuel.  
  
 [LoadStringRCEx, fonction](loadstringrcex-function.md)  
 Action déconseillée. Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)](lpoverlapped-completion-routine-function-pointer.md)  
 Action déconseillée. Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.  
  
 [LPTHREAD_START_ROUTINE (pointeur fonction)](lpthread-start-routine-function-pointer.md)  
 Action déconseillée. Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.  
  
 [RunDll32ShimW, fonction](rundll32shimw-function.md)  
 Action déconseillée. Exécute la commande spécifiée.  
  
 [WAITORTIMERCALLBACK (pointeur fonction)](waitortimercallback-function-pointer.md)  
 Action déconseillée. Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.  
  
## <a name="infrastructure-functions"></a>Fonctions d’infrastructure  
 Les fonctions de cette section sont destinées à être utilisées par l' .NET Framework uniquement.  
  
 [_CorDllMain, fonction](cordllmain-function.md)  
 Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.  
  
 [_CorExeMain, fonction](corexemain-function.md)  
 Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.  
  
 [_CorExeMain2, fonction](corexemain2-function.md)  
 Exécute le point d’entrée dans le code mappé en mémoire spécifié. Cette fonction est appelée par le chargeur du système d’exploitation.  
  
 [_CorImageUnloading, fonction](corimageunloading-function.md)  
 Notifie le chargeur lorsque les images de modules managés sont déchargées.  
  
 [_CorValidateImage, fonction](corvalidateimage-function.md)  
 Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de l'hébergement .NET Framework 4](net-framework-4-hosting-global-static-functions.md)
