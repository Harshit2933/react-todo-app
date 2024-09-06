# react-todo-app
import React, { useState, useEffect } from "react";
import TodoList from "./TodoList";
function App() {
Tasks] = useState(() => {
    // Load tasks from localStorage if they exist
    const savedTasks = localStorage.getItem("tasks");
    return savedTasks ? JSON.parse(savedTasks) : [];
  });
  const [taskText, setTaskText] = useState("");
  const [filter, setFilter] = useState("all");

  useEffect(() => {
    // Save tasks to localStorage whenever tasks change
    localStorage.setItem("tasks", JSON.stringify(tasks));
  }, [tasks]);

  const addTask = () => {
    if (taskText.trim() === "") return;
    const newTask = {
      id: Date.now(),
      text: taskText,
      completed: false,
    };
    setTasks([...tasks, newTask]);
    setTaskText(""); // Clear input
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id));
  };

  const toggleCompleteTask = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, completed: !task.completed } : task
      )
    );
  };

  const filteredTasks = tasks.filter((task) => {
    if (filter === "completed") return task.completed;
    if (filter === "incomplete") return !task.completed;
    return true;
  });

  return (
    <div className="app">
      <h1>To-Do List</h1>
      <div className="task-input">
        <input
          type="text"
          value={taskText}
          onChange={(e) => setTaskText(e.target.value)}
          placeholder="Add a new task..."
        />
        <button onClick={addTask}>Add Task</button>
      </div>
      <div className="filters">
        <button onClick={() => setFilter("all")}>All</button>
        <button onClick={() => setFilter("completed")}>Completed</button>
        <button onClick={() => setFilter("incomplete")}>Incomplete</button>
      </div>
      <TodoList
        tasks={filteredTasks}
        deleteTask={deleteTask}
        toggleCompleteTask={toggleCompleteTask}
   
        import React from "react";
        import TodoItem from "./TodoItem";
        
        function TodoList({ tasks, deleteTask, toggleCompleteTask }) {
          return (
            <ul className="todo-list">
              {tasks.map((task) => (
                <TodoItem
                  key={task.id}
                  task={task}
                  deleteTask={deleteTask}
                  toggleCompleteTask={toggleCompleteTask}
                />
              ))}
            </ul>
          );
        }
        
        export default TodoList;
        import React from "react";

        function TodoItem({ task, deleteTask, toggleCompleteTask }) {
          return (
            <li className={`todo-item ${task.completed ? "completed" : ""}`}>
              <span onClick={() => toggleCompleteTask(task.id)}>{task.text}</span>
              <button onClick={() => deleteTask(task.id)}>Delete</button>
            </li>
          );
        }
        
        export default TodoItem;
        .app {
            text-align: center;
            font-family: Arial, sans-serif;
          }
          
          .task-input {
            margin: 20px 0;
          }
          
          .filters {
            margin: 10px 0;
          }
          
          .todo-list {
            list-style: none;
            padding: 0;
          }
          
          .todo-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid #ddd;
          }
          
          .todo-item.completed span {
            text-decoration: line-through;
            color: #999;
          }
          
          button {
            background-color: #ff6b6b;
            border: none;
            color: white;
            padding: 5px 10px;
            cursor: pointer;
          }
          
          button:hover {
            background-color: #ff4c4c;
          }
          git init
git add .
git commit -m "Initial commit for todo app"
git remote add origin <your-repo-url>
git push -u origin master
git init
git add .
git commit -m "Initial commit for todo app"
git remote add origin <your-repo-url>
git push -u origin master
npm install
npm start

