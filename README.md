package com.forum.model;

import java.time.Instant;
import java.time.LocalDateTime;
import java.time.ZoneId;

public class User {
    private int id;
    private String username;
    private String password; 
    private String email;
    private long creationTimestamp; 

    public User(String username, String password, String email) {
        this.username = username;
        this.password = password;
        this.email = email;
        this.creationTimestamp = System.currentTimeMillis(); 
    }

    // 5-parameter constructor used by DAO to fetch from DB
    public User(int id, String username, String password, String email, long creationTimestamp) {
        this.id = id;
        this.username = username;
        this.password = password;
        this.email = email;
        this.creationTimestamp = creationTimestamp;
    }

    // --- Getters ---
    public int getId() { return id; }
    public String getUsername() { return username; }
    public String getPassword() { return password; }
    public String getEmail() { return email; }
    public long getCreationTimestamp() { return creationTimestamp; }

    public LocalDateTime getFormattedCreationDate() {
        return LocalDateTime.ofInstant(Instant.ofEpochMilli(creationTimestamp), ZoneId.systemDefault());
    }
    
    // --- Setters ---
    public void setId(int id) { this.id = id; }
    public void setPassword(String password) { this.password = password; }
}
