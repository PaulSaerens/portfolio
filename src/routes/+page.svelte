<script module>
</script>

<script>
  import Header from "$lib/header.svelte";
  import Timeline from "$lib/timeline.svelte"

    const timelineItems = [
    {
      title: 'Événement 1',
      date: 'Janvier 2025',
      description: 'Description du premier événement'
    },
    {
      title: 'Événement 2',
      date: 'Février 2025',
      description: 'Description du deuxième événement'
    },
    {
      title: 'Événement 3',
      date: 'Mars 2025',
      description: 'Description du troisième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    },
    {
      title: 'Événement 4',
      date: 'Avril 2025',
      description: 'Description du quatrième événement'
    }
  ];

</script>

<div class='header'>
  <Header />
</div>

<div class='body'>
  <Timeline items={timelineItems}/>
</div>


<style>
  .header {
    width: 100%;
    height: 40vh;
    margin: 0;
  }

  .body {
    width: 75%;
    margin: 0 auto;
    overflow-x: hidden;
  }
</style>
