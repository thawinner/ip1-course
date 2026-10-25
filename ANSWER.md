1. Index as key: after filtering, Vue reuses components by position, so a card's local state (like an open details panel) ends up on a different event.
2. Computed vs function: a computed is cached and only recalculates when search, category or events change. A function runs again on every re-render.
3. Emit vs mutate: props are read-only, and only the parent that owns the data should change it. It also keeps EventCard reusable, because the parent decides what "book" means.
4. Destructuring reactive: destructuring copies booked out as a plain number, which loses the reactivity. Use toRefs or ev.booked++ instead.
5. Where myBookings lives: in App, because the header and the events need it, and App is the nearest common parent. EventList's cards come and go when you filter.