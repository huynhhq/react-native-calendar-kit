---
sidebar_position: 6
---

# Initial Time Position

The `initialHour` prop allows you to set a custom initial scroll position for the calendar timeline. This is particularly useful for business applications where you want the calendar to start at working hours (e.g., 8:00 AM) instead of the current time.

## Basic Usage

```tsx
import { CalendarContainer, CalendarHeader, CalendarBody } from '@howljs/calendar-kit';

const MyCalendar = () => {
  return (
    <CalendarContainer
      scrollToNow={false}
      initialHour={8}
    >
      <CalendarHeader />
      <CalendarBody />
    </CalendarContainer>
  );
};
```

## Examples

### Business Hours Calendar

Start the calendar at 9:00 AM for a typical business day:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialHour={9}
  start={8 * 60}  // 8:00 AM
  end={18 * 60}   // 6:00 PM
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Half-Hour Precision

You can use decimal values to specify minutes:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialHour={8.5}  // 8:30 AM
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Different Time Formats

```tsx
// 2:15 PM
<CalendarContainer
  scrollToNow={false}
  initialHour={14.25}
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>

// 6:45 PM
<CalendarContainer
  scrollToNow={false}
  initialHour={18.75}
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Combined with Custom Date

Set both initial date and time:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialDate="2024-03-15"
  initialHour={10}
  minDate="2024-01-01"
  maxDate="2024-12-31"
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

## Important Notes

### Prerequisites

- **`scrollToNow` must be `false`**: The `initialHour` prop only works when `scrollToNow={false}`. If `scrollToNow` is `true` (default), the calendar will scroll to the current time instead.

### Hour Format

- **24-hour format**: Use 24-hour format (0-23)
- **Decimal minutes**: Use decimals for minutes (e.g., `8.5` = 8:30, `14.25` = 2:15)
- **Valid range**: The hour should be within your calendar's time range defined by `start` and `end` props

### Conversion Examples

| Time | Hour Value | Calculation |
|------|------------|-------------|
| 8:00 AM | `8` | 8 |
| 8:30 AM | `8.5` | 8 + 30/60 |
| 8:15 AM | `8.25` | 8 + 15/60 |
| 2:00 PM | `14` | 14 |
| 2:30 PM | `14.5` | 14 + 30/60 |
| 6:45 PM | `18.75` | 18 + 45/60 |

### Behavior

- **No animation**: The initial scroll happens without animation for better performance
- **Fallback**: If `initialHour` is not specified and `scrollToNow={false}`, the calendar will not auto-scroll
- **Validation**: If the specified hour is outside the calendar's time range, the scroll may not work as expected

## Use Cases

### Meeting Scheduler

Perfect for meeting scheduling applications:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialHour={9}
  start={8 * 60}    // Start at 8 AM
  end={17 * 60}     // End at 5 PM
  timeInterval={30} // 30-minute intervals
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Event Planning

For event planning with specific time focus:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialHour={18}  // 6 PM for evening events
  numberOfDays={3}
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Medical Appointments

For medical appointment systems:

```tsx
<CalendarContainer
  scrollToNow={false}
  initialHour={8}   // Start of clinic hours
  start={8 * 60}    // 8:00 AM
  end={20 * 60}     // 8:00 PM
  timeInterval={15} // 15-minute slots
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

This feature provides a better user experience by showing the most relevant time period immediately when the calendar loads.
