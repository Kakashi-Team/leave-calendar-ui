import React, { useState } from "react";
import Calendar from "react-calendar";
import "react-calendar/dist/Calendar.css";

export default function App() {
  const [date, setDate] = useState(new Date());
  const [showForm, setShowForm] = useState(false);
  const [type, setType] = useState("");

  const onDateClick = (value) => {
    setDate(value);
    setShowForm(true);
  };

  const handleSubmit = () => {
    alert(`You applied for a ${type} on ${date.toDateString()}`);
    setShowForm(false);
  };

  return (
    <div style={{ textAlign: "center", padding: "30px" }}>
      <h1>Team Leave Calendar</h1>
      <Calendar onClickDay={onDateClick} value={date} />

      {showForm && (
        <div style={{ marginTop: "20px" }}>
          <h3>{date.toDateString()}</h3>
          <select onChange={(e) => setType(e.target.value)} value={type}>
            <option value="">-- Select Type --</option>
            <option value="Leave">Leave</option>
            <option value="WFH">Work From Home</option>
            <option value="Half Day">Half Day</option>
          </select>
          <button onClick={handleSubmit} style={{ marginLeft: "10px" }}>
            Apply
          </button>
        </div>
      )}
    </div>
  );
}
