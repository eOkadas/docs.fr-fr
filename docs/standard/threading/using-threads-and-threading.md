---
title: Utilisation des threads et du threading
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a12ff92202ace69cb80ff59d6afcb5d8f8243
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960381"
---
# <a name="using-threads-and-threading"></a>Utilisation des threads et du threading

Avec .NET, vous pouvez écrire des applications qui effectuent plusieurs opérations en même temps. Les opérations présentant le risque d’accaparer les ressources d’autres opérations peuvent s’exécuter sur des threads distincts : ce processus est appelé *multithreading* ou *threading libre*.  
  
Les applications qui utilisent le multithreading sont plus réactives aux entrées utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads distincts. Le multithreading est également utile quand vous créez des applications scalables, car vous pouvez ajouter des threads au fil de l’augmentation de la charge de travail.

> [!NOTE]
> Si vous avez besoin de plus de contrôle sur le comportement des threads de l’application, vous pouvez gérer vous-même les threads. Toutefois, à compter de .NET Framework 4, la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>, et un nouveau modèle de programmation basé sur le concept de tâches plutôt que de threads. Pour plus d’informations, consultez [Programmation parallèle](../parallel-programming/index.md) et [Bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Procédure : créer et démarrer un nouveau thread

Pour créer un thread, vous devez créer une instance de la classe <xref:System.Threading.Thread?displayProperty=nameWithType> et fournir au constructeur le nom de la méthode que vous souhaitez exécuter sur un nouveau thread. Pour démarrer un thread créé, appelez la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Pour plus d’informations et pour obtenir des exemples, consultez l’article [Création de threads et passage de données au démarrage](creating-threads-and-passing-data-at-start-time.md) et la référence de l’API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Procédure : arrêter un thread

Pour mettre fin à l’exécution d’un thread, utilisez la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Cette méthode lève une <xref:System.Threading.ThreadAbortException> sur le thread sur lequel elle est appelée. Pour plus d’informations, consultez [Destruction de threads](destroying-threads.md).

À compter de .NET Framework 4, vous pouvez utiliser <xref:System.Threading.CancellationToken?displayProperty=nameWithType> pour annuler un thread de manière coopérative. Pour plus d’informations, consultez [Annulation dans les threads managés](cancellation-in-managed-threads.md).

Utilisez la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> pour faire en sorte que le thread appelant attende l’arrêt du thread sur lequel la méthode est appelée.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Procédure : suspendre ou interrompre un thread

Vous utilisez la méthode <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> pour suspendre le thread actif pendant un certain laps de temps. Vous pouvez interrompre un thread bloqué en appelant la méthode <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [Suspension et interruption de threads](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Propriétés du thread

Le tableau suivant présente certaines des propriétés de <xref:System.Threading.Thread> :  
  
|Property|Description|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Retourne `true` si un thread a été démarré et ne s’est pas encore arrêté normalement ou n’a pas été abandonné.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtient ou définit une valeur booléenne qui indique si un thread est un thread d’arrière-plan. Les threads d’arrière-plan ressemblent aux threads de premier plan, mais un thread d’arrière-plan n’empêche pas un processus de s’arrêter. Une fois que tous les threads de premier plan appartenant à un processus sont arrêtés, le common language runtime met fin au processus en appelant la méthode <xref:System.Threading.Thread.Abort%2A> sur les threads d’arrière-plan encore actifs. Pour plus d’informations, consultez [Threads de premier plan et d’arrière-plan](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Obtient ou définit le nom d’un thread. Généralement utilisé pour découvrir des threads individuels lors du débogage.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtient ou définit une valeur <xref:System.Threading.ThreadPriority> utilisée par le système d’exploitation pour classer par priorité la planification des threads. Pour plus d’informations, consultez [Planification des threads](scheduling-threads.md) et la référence de <xref:System.Threading.ThreadPriority>.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Obtient une valeur <xref:System.Threading.ThreadState> contenant les états actuels d’un thread.|  

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Threads et threading](threads-and-threading.md)
- [Programmation parallèle](../parallel-programming/index.md)
