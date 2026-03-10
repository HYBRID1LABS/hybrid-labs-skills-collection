# Appointment Booking System

**Complete appointment booking and management for service businesses**

---

## 🎯 Overview

Generic appointment booking system for beauty salons, clinics, studios, and photo booths. Handles booking requests, calendar sync, conflict detection, automated reminders, no-show tracking, and daily schedule reports.

---

## ✨ Features

- **Booking Intake** - Web forms and API
- **Calendar Sync** - Google Calendar, Outlook
- **Conflict Detection** - Prevent double-booking
- **Automated Reminders** - 24h and 2h before appointment
- **No-Show Tracking** - Track and flag repeat offenders
- **Daily Reports** - Schedule summaries

---

## 📦 Installation

```bash
npm install @hybrid-labs/appointment-booking-system
```

---

## 🚀 Quick Start

```javascript
const booking = require('@hybrid-labs/appointment-booking-system');

// Initialize
await booking.init({
  calendar: 'google',
  timezone: 'Europe/Madrid',
  workingHours: { start: 9, end: 18 }
});

// Create booking
const appointment = await booking.create({
  customerName: 'Jane Smith',
  customerEmail: 'jane@example.com',
  customerPhone: '+34600000000',
  service: 'Consultation',
  dateTime: '2026-03-15T10:00:00Z',
  duration: 60,
  notes: 'First-time customer'
});

// Send confirmation
await booking.sendConfirmation(appointment.id);

// Send reminders (automatic)
await booking.sendReminders({
  appointmentId: appointment.id,
  times: ['24h', '2h']
});

// Get daily schedule
const schedule = await booking.getDailySchedule({
  date: '2026-03-15'
});
console.log(schedule);
// { appointments: [...], totalHours: 6, utilization: 0.75 }

// Mark as no-show
await booking.markNoShow(appointment.id);
```

---

## 📊 Booking Workflow

1. **Customer Books** → Web form or API
2. **Conflict Check** → Verify availability
3. **Confirmation Sent** → Email/SMS
4. **Reminders** → 24h and 2h before
5. **Appointment** → Check-in/out
6. **Follow-Up** → Request review or rebook

---

## 🎨 Advanced Usage

### Recurring Appointments

```javascript
const recurring = await booking.createRecurring({
  customerName: 'John Doe',
  service: 'Weekly Therapy',
  dateTime: '2026-03-15T10:00:00Z',
  duration: 60,
  recurrence: {
    frequency: 'weekly',
    count: 10
  }
});
```

### Waitlist Management

```javascript
await booking.addToWaitlist({
  service: 'Consultation',
  preferredDates: ['2026-03-15', '2026-03-16'],
  customerEmail: 'waitlist@example.com'
});

// Notify when slot opens
booking.on('slotOpened', async (slot) => {
  const waitlistCustomer = await booking.getWaitlist(slot.service);
  await booking.notifyAvailability(waitlistCustomer, slot);
});
```

### Analytics

```javascript
const analytics = await booking.getAnalytics({
  startDate: '2026-03-01',
  endDate: '2026-03-31'
});
console.log(analytics);
// {
//   totalBookings: 150,
//   noShows: 12,
//   noShowRate: 0.08,
//   revenue: 15000,
//   utilization: 0.72
// }
```

---

## 🔧 Configuration

```javascript
await booking.init({
  calendar: 'google',
  timezone: 'Europe/Madrid',
  workingHours: { start: 9, end: 18, days: [1, 2, 3, 4, 5] },
  slotDuration: 30, // minutes
  bufferTime: 15, // minutes between appointments
  reminders: {
    enabled: true,
    times: ['24h', '2h'],
    method: 'email' // or 'sms'
  },
  noShowPolicy: {
    maxNoShows: 3,
    action: 'block' // or 'warn'
  }
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
