document.addEventListener('DOMContentLoaded', function () {
  const weekPeriodDiv = document.getElementById('weekPeriod');
  const calculateButton = document.getElementById('calculateButton');
  const dateInput = document.getElementById('dateInput');
  
  const dateForWeekDiv = document.getElementById('dateForWeek');
  const dateForWeekButton = document.getElementById('dateForWeekButton');
  const weekInput = document.getElementById('weekInput');

  calculateButton.addEventListener('click', function () {
    const inputDate = dateInput.value;
    if (isValidDate(inputDate)) {
      const [day, month, year] = inputDate.split('/').map(Number);
      const date = new Date(year + 2000, month - 1, day); // Adjust for 2-digit year
      showWeekPeriod(date);
    } else {
      weekPeriodDiv.textContent = 'Invalid date format. Please use dd/mm/yy.';
    }
  });

  dateForWeekButton.addEventListener('click', function () {
    const weekNumber = parseInt(weekInput.value, 10);
    if (!isNaN(weekNumber) && weekNumber > 0) {
      const date = getDateForWeek(weekNumber);
      dateForWeekDiv.textContent = `Week ${weekNumber} starts on ${date.toLocaleDateString()}`;
    } else {
      dateForWeekDiv.textContent = 'Invalid week number.';
    }
  });

  function isValidDate(dateString) {
    const regex = /^\d{2}\/\d{2}\/\d{2}$/;
    if (!dateString.match(regex)) return false;
    const [day, month, year] = dateString.split('/').map(Number);
    const date = new Date(year + 2000, month - 1, day);
    return date.getFullYear() === year + 2000 && date.getMonth() === month - 1 && date.getDate() === day;
  }

  function showWeekPeriod(date) {
    const startDate = new Date('2024-03-03'); // Start date is March 3rd, 2024
    let diffInTime = date.getTime() - startDate.getTime();
    let diffInDays = Math.floor(diffInTime / (1000 * 3600 * 24));

    if (diffInDays < 0) { // Handle dates before 2024
      const previousYearStartDate = new Date(date.getFullYear(), 2, 3); // Start date of the given year
      diffInTime = date.getTime() - previousYearStartDate.getTime();
      diffInDays = Math.floor(diffInTime / (1000 * 3600 * 24));
      const weeksSinceYearStart = Math.floor(diffInDays / 7) + 1;
      const totalWeeks = 52; // Assuming each year has 52 weeks
      const currentWeek = weeksSinceYearStart > 0 ? weeksSinceYearStart : totalWeeks + weeksSinceYearStart;
      const currentPeriod = Math.ceil(currentWeek / 4);
      const weekOfPeriod = (currentWeek - 1) % 4 + 1;
      weekPeriodDiv.textContent = `Week ${weekOfPeriod} of Period ${currentPeriod}`;
    } else {
      const currentWeek = Math.floor(diffInDays / 7) + 1;
      const currentPeriod = Math.ceil(currentWeek / 4);
      const weekOfPeriod = (currentWeek - 1) % 4 + 1;
      weekPeriodDiv.textContent = `Week ${weekOfPeriod} of Period ${currentPeriod}`;
    }
  }

  function getDateForWeek(weekNumber) {
    const startDate = new Date('2024-03-03'); // Start date is March 3rd, 2024
    const targetDate = new Date(startDate.getTime());
    targetDate.setDate(startDate.getDate() + (weekNumber - 1) * 7);
    return targetDate;
  }

  // Initialize with current date
  showWeekPeriod(new Date());
});
