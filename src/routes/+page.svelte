<script>
  export const tableHeadings = [
    {
      monthDay: 25,
      weekDay: 'Thu'
    },
    {
      monthDay: 26,
      weekDay: 'Fri'
    },
    {
      monthDay: 27,
      weekDay: 'Sat'
    },
    {
      monthDay: 28,
      weekDay: 'Sun'
    },
    {
      monthDay: 29,
      weekDay: 'Mon'
    },
    {
      monthDay: 30,
      weekDay: 'Tue'
    },
    {
      monthDay: 31,
      weekDay: 'Wed'
    },
    {
      monthDay: 1,
      weekDay: 'Thu'
    },
    {
      monthDay: 2,
      weekDay: 'Fri'
    },
    {
      monthDay: 3,
      weekDay: 'Sat'
    },
    {
      monthDay: 4,
      weekDay: 'Sun'
    },
    {
      monthDay: 5,
      weekDay: 'Mon'
    },
    {
      monthDay: 6,
      weekDay: 'Tue'
    },
    {
      monthDay: 7,
      weekDay: 'Wed'
    },
    {
      monthDay: 8,
      weekDay: 'Thu'
    },
    {
      monthDay: 9,
      weekDay: 'Fri'
    },
    {
      monthDay: 10,
      weekDay: 'Sat'
    },
    {
      monthDay: 11,
      weekDay: 'Sun'
    },
    {
      monthDay: 12,
      weekDay: 'Mon'
    },
    {
      monthDay: 13,
      weekDay: 'Tue'
    },
    {
      monthDay: 14,
      weekDay: 'Wed'
    },
    {
      monthDay: 15,
      weekDay: 'Thu'
    },
    {
      monthDay: 16,
      weekDay: 'Fri'
    },
    {
      monthDay: 17,
      weekDay: 'Sat'
    },
    {
      monthDay: 18,
      weekDay: 'Sun'
    },
    {
      monthDay: 19,
      weekDay: 'Mon'
    },
    {
      monthDay: 20,
      weekDay: 'Tue'
    },
    {
      monthDay: 21,
      weekDay: 'Wed'
    },
    {
      monthDay: 22,
      weekDay: 'Thu'
    },
    {
      monthDay: 23,
      weekDay: 'Fri'
    },
  ]

  export const bedRows = [
    {
      bedName: 'r1 b1',
      schedule: [
        {
          type: 'booking',
          bookingID: '1c71346a-fb07-11ed-be56-0242ac120002',
          length: 30,
          personName: 'Darius Salom',
          startDate: '2023-05-25',
          startDateFormatted: '25 May',
          endDate: '2023-06-26',
          endDateFormatted: '26 Jun',
        },
      ]
    },
    {
      bedName: 'r2 b1',
      schedule: [
        {
          type: 'booking',
          bookingID: '78a5d6ce-fbab-11ed-be56-0242ac120002',
          length: 8,
          personName: 'Ali Mahan',
          startDate: '2023-04-12',
          startDateFormatted: '12 Apr',
          endDate: '2023-05-30',
          endDateFormatted: '30 May',
        },
        {
          type: 'void',
          length: 2,
          startDate: '2023-05-31',
          startDateFormatted: '31 May',
          endDate: '2023-06-01',
          endDateFormatted: '1 Jun',
        },
        {
          type: 'open',
          length: 15,
          startDate: '2023-06-02',
          startDateFormatted: '2 Jun',
          endDate: '2023-06-18',
          endDateFormatted: '18 Jun',
        },
        {
          type: 'booking',
          bookingID: 'd1952d10-fbb1-11ed-be56-0242ac120002',
          length: 30,
          personName: 'James Brown',
          startDate: '2023-06-19',
          startDateFormatted: '19 Jun',
          endDate: '2023-07-19',
          endDateFormatted: '19 Jul',
        },
      ]
    },
    {
      bedName: 'r3 b1',
      schedule: [
        {
          type: 'booking',
          bookingID: '1c71346a-fb07-11ed-be56-0242ac120001',
          length: 20,
          personName: 'Aniko Gaal',
          startDate: '2023-05-25',
          startDateFormatted: '25 May',
          endDate: '2023-06-16',
          endDateFormatted: '16 Jun',
        },
        {
          type: 'booking',
          bookingID: '1c71346a-fb07-11ed-be56-0242ac120001',
          length: 20,
          personName: 'Adam Hughes',
          startDate: '2023-06-17',
          startDateFormatted: '17 Jun',
          endDate: '2023-08-17',
          endDateFormatted: '17 Jul',
        },
      ]
    },
  ]
</script>

<h1>30 day Scheduler Prototype</h1>

<section aria-label="Overview calendar">
  <div class="scrollable">
    <table cellspacing="0">
      <thead>
        <th>Room/Bed</th>
        {#each tableHeadings as tableHeading}
          {#if tableHeading.weekDay === 'Sat' || tableHeading.weekDay === 'Sun'}
            <th class="weekend">{tableHeading.monthDay}</th>
          {:else}
            <th>{tableHeading.monthDay}</th>
          {/if}
        {/each}
      </thead>

      <tbody>
        {#each bedRows as bedRow}
          <tr>
            <th class="bed-heading" scope="row">{bedRow.bedName}</th>

            {#each bedRow.schedule as booking}
              {#if booking.type === 'booking'}
                <td class="booking booking-id-{booking.bookingID}" colspan="{booking.length}">
                  <a href="/booking/{booking.bookingID}" title="{booking.personName} ({booking.startDateFormatted} - {booking.endDateFormatted}">{booking.personName} ({booking.startDateFormatted} - {booking.endDateFormatted})</a>
                </td>
              {:else if booking.type === 'open'}
                <td class="open" colspan="{booking.length}">
                  
                </td>
              {:else}
                <td class="void" colspan="{booking.length}">
                  
                </td>
              {/if}
            {/each}
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</section>


<style>
  .scrollable {
    position: relative;
    overflow: scroll;
  }

  .scrollable table {
    width: 900px;
  }

  td {
    border: 1px solid #ccc;
    border-bottom: 1px solid #1f1f1f;
  }

  .clash {
    background-color: red;
  }

  .clash p {
    display: block !important;
  }

  th {
    font-size: 10px;
    width: 20px;
  }

  th.bed-heading {
    width: 40px;
  }

  .room {
    font-size: 8px;
  }

  .booking {
    position: relative;
    background-color: rgba(86, 148, 202, 0.25);
    color: #000;
    font-size: 14px;
  }

  .open {
    background-color: #fff;
    font-size: 0;
  }

  .void {
    background-color: rgba(177, 180, 182, 0.5);
  }

  .weekend {
    background: #ebebeb;
  }

</style>
