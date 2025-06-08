---
sidebar_position: 5
---

# Hide Out of Range Dates

When using custom `numberOfDays` (less than 7), the calendar normally shows complete weeks which may include dates outside your specified `minDate` and `maxDate` range. The `hideOutOfRangeDates` prop allows you to hide these out-of-range dates and only show dates within your specified range.

## Basic Usage

```tsx
import { CalendarContainer, CalendarHeader, CalendarBody } from '@howljs/calendar-kit';

const MyCalendar = () => {
  return (
    <CalendarContainer
      numberOfDays={3}
      minDate="2024-01-15"
      maxDate="2024-01-20"
      hideOutOfRangeDates={true}
    >
      <CalendarHeader />
      <CalendarBody />
    </CalendarContainer>
  );
};
```

## Behavior Comparison

### Default Behavior (`hideOutOfRangeDates={false}`)

When `hideOutOfRangeDates` is `false` (default), the calendar shows complete weeks:

- **Date Range**: January 15-20, 2024 (6 days)
- **Displayed**: Full weeks containing these dates (potentially 14 days)
- **Navigation**: Week-based scrolling

### With `hideOutOfRangeDates={true}`

When `hideOutOfRangeDates` is `true`, the calendar only shows dates within the range:

- **Date Range**: January 15-20, 2024 (6 days)
- **Displayed**: Only the 6 days within the range
- **Navigation**: Day-by-day scrolling

## Use Cases

### Limited Date Range Calendar

Perfect for calendars with a specific date range, such as event schedules or booking systems:

```tsx
<CalendarContainer
  numberOfDays={5}
  minDate="2024-03-01"
  maxDate="2024-03-31"
  hideOutOfRangeDates={true}
  scrollToNow={false}
  initialDate="2024-03-01"
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

### Custom Week View

Create a custom week view that doesn't extend beyond your data range:

```tsx
<CalendarContainer
  numberOfDays={7}
  minDate="2024-01-01"
  maxDate="2024-12-31"
  hideOutOfRangeDates={true}
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

## Important Notes

1. **Navigation**: When `hideOutOfRangeDates` is enabled, navigation automatically switches to day-by-day scrolling instead of week-based scrolling.

2. **Compatibility**: This feature works with:
   - Custom `numberOfDays` (1-7)
   - `hideWeekDays` prop
   - All calendar themes and customizations

3. **Performance**: Only affects the date calculation logic, no impact on rendering performance.

4. **Single Day Mode**: In single day mode (`numberOfDays={1}`), this prop has no effect since single day mode already respects the date range.

## Example with Hidden Weekdays

You can combine `hideOutOfRangeDates` with `hideWeekDays` for more control:

```tsx
<CalendarContainer
  numberOfDays={5}
  minDate="2024-01-15"
  maxDate="2024-01-25"
  hideOutOfRangeDates={true}
  hideWeekDays={[6, 7]} // Hide weekends
>
  <CalendarHeader />
  <CalendarBody />
</CalendarContainer>
```

This will show only weekdays within the specified date range.
