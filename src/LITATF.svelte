<script lang="ts">
  import AllMatsLink from './components/AllMatsLink.svelte';
  import ScheduleBlock from './components/ScheduleBlock.svelte';

  const data = [
  { daynum: '1', title: 'June 26th', activities: [{ name: 'PD Bootcamp Welcome', time: '10:00AM - 10:15AM', duration: '15', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1bpFT61uzdZ3Nc9qmL0SIKO0vXffmmTqaAjLFRi8hzFk/edit?usp=sharing' },]},{ name: 'Team Building', time: '10:15AM - 10:45AM', duration: '30', actType: 'teambuilding', links: []},{ name: 'Overview of the SI', time: '10:45AM - 11:00AM', duration: '15', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1m0nJl8G_XDjBl-09rmSvRwJhuENe-itqOePQzZNX2vc/edit?usp=sharing' },]},{ name: 'Roles and Responsibilities', time: '11:00AM - 11:15AM', duration: '15', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1obHwhybPjAbR5qdLeSyqRfE6NnSH4RMFgyW3px7BsVE/edit?usp=sharing' },]},{ name: 'BREAK', time: '11:15AM - 11:30AM', duration: '15', actType: 'misc', links: []},{ name: 'HR Onboarding', time: '11:30AM - 12:00PM', duration: '30', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1Aa1O2MkLSygCxesAGoMgZkBftur7wYY12w0MIMYvgRo/edit?usp=sharing' },]},{ name: 'Escalation Policy', time: '12:00PM - 12:30PM', duration: '30', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1Splnie7GPW2e1YXsOx7lU18zZDONHsUyKB7fLK3Qi0I/edit?usp=sharing' },]},{ name: 'LUNCH', time: '12:30PM - 01:30PM', duration: '60', actType: 'misc', links: []},{ name: 'Team Building', time: '01:30PM - 02:00PM', duration: '30', actType: 'teambuilding', links: []},{ name: 'Google Classroom', time: '02:00PM - 02:30PM', duration: '30', actType: 'coreskill', links: [{ displayText: 'Google Classroom', linkURL: 'https://classroom.google.com/' },]},{ name: 'BREAK', time: '02:30PM - 02:45PM', duration: '15', actType: 'misc', links: []},{ name: 'Microteaching', time: '02:45PM - 03:45PM', duration: '60', actType: 'lecture', links: [{ displayText: 'Microteaching Feedback Form', linkURL: 'https://forms.gle/MCh1tzvDL37kscE19' },{ displayText: 'Microteaching Feedback Form (Responses)', linkURL: 'https://docs.google.com/spreadsheets/d/1ZWGlQuqvuYDmr0AyCm9yjQZWeXwxRjVqhuaK1LiBcX8/edit?usp=sharing' },]},{ name: 'BREAK', time: '03:45PM - 04:00PM', duration: '15', actType: 'misc', links: []},{ name: 'Orientation Overview', time: '04:00PM - 04:30PM', duration: '30', actType: 'project', links: [{ displayText: 'Run of Show', linkURL: 'https://docs.google.com/document/d/16NyCzqEP8hCwJgYfuXMh94jq3_gpSQKAB55UyaFAO30/edit?usp=sharing' },{ displayText: 'Orientation Deck', linkURL: 'https://docs.google.com/presentation/d/10XF3iIBQ2ILSM7je_B1QkkC2Noebh2NNQ7ypTW8Wf2k/edit?usp=sharing' },]},{ name: 'Orientation Prep', time: '04:30PM - 05:15PM', duration: '45', actType: 'project', links: []},{ name: 'Exit Survey', time: '05:15PM - 05:30PM', duration: '15', actType: 'survey', links: []},{ name: 'Office Hours', time: '05:30PM - 06:00PM', duration: '30', actType: 'officehours', links: []},],},
  { daynum: '2', title: 'June 27th', activities: [{ name: 'Team Building', time: '10:00AM - 10:30AM', duration: '30', actType: 'teambuilding', links: []},{ name: 'AI in Education', time: '10:30AM - 11:15AM', duration: '45', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1L9xhqsfdJNVbQkoxVkKwJ6uQ2ybEEmdTtCDy3n7IbZ8/edit?usp=sharing' },{ displayText: 'TA Dante', linkURL: 'https://ta-dante-asc.app/s/6-Week_SI?d=PCUv4R7J' },]},{ name: 'BREAK', time: '11:15AM - 11:30AM', duration: '15', actType: 'misc', links: []},{ name: 'IEP / 504 Overview', time: '11:30AM - 12:30PM', duration: '60', actType: 'coreskill', links: [{ displayText: 'Presentation Slides', linkURL: 'https://docs.google.com/presentation/d/1IukJ4i1dGsybNBcAUxuJiOez-HUpGypLyd8GU6rbJUg/edit?usp=sharing' },{ displayText: '[2025] Effective Strategies for Neurodiversity', linkURL: 'https://drive.google.com/file/d/1yYHNk3dnjaYpeayZivGKucQ_UK5kxWl2/view?usp=sharing' },]},{ name: 'LUNCH', time: '12:30PM - 01:30PM', duration: '60', actType: 'misc', links: []},{ name: 'Team Building', time: '01:30PM - 02:00PM', duration: '30', actType: 'teambuilding', links: []},{ name: 'Roles and Responsibilities II', time: '02:00PM - 02:30PM', duration: '30', actType: 'lecture', links: []},{ name: 'BREAK', time: '02:30PM - 02:45PM', duration: '15', actType: 'misc', links: []},{ name: 'Hack-AI-thon', time: '02:45PM - 04:00PM', duration: '75', actType: 'lecture', links: [{ displayText: 'Hack-AI-thon Instructions', linkURL: 'https://docs.google.com/document/d/1QRU26bGaxCx7y_1Iytva3K-3HfmQgj4UJRARzPNuq40/edit?usp=sharing' },]},{ name: 'BREAK', time: '04:00PM - 04:15PM', duration: '15', actType: 'misc', links: []},{ name: 'Orientation Prep', time: '04:15PM - 05:00PM', duration: '45', actType: 'project', links: []},{ name: 'ORIENTATION BREAK', time: '05:00PM - 06:00PM', duration: '60', actType: 'misc', links: []},{ name: 'Orientation', time: '06:00PM - 08:00PM', duration: '120', actType: 'project', links: []},],},
  ];
</script>

<ul class="collapsible">
  {#each data as day}
    <li>
      <div
        id={`LITATF-day-${day.daynum}-header`}
        class="collapsible-header title"
        data-state="closed"
      >
        <span>Day {day.daynum} -</span>
        <span class="dayofWeek"
          >&nbsp;
          {#if day.daynum === '1'}
            Wednesday
          {:else if day.daynum === '2'}
            Thursday
          {/if}
        </span>
        <span class="titleFix">&nbsp;{day.title}</span>
      </div>
      <div class="collapsible-body">
        {#each day.activities as activity}
          <ScheduleBlock
            name={activity.name}
            time={activity.time}
            duration={activity.duration}
            actType={activity.actType}
            links={activity.links}
            daynum={day.daynum}
          />
        {/each}
      </div>
    </li>
  {/each}
  <li class="litatf-all-links all-links">
    <div class="collapsible-header">
      <div class="title">All PD Materials</div>
    </div>
    <div class="collapsible-body">
      <ul class="collection">
        {#each data as day}
          {#each day.activities as activity}
            {#if activity.links.length > 0}
              <AllMatsLink
                classes={`day${day.daynum}-all-links`}
                actname={activity.name}
                links={activity.links}
              />
            {/if}
          {/each}
        {/each}
      </ul>
    </div>
  </li>
</ul>
