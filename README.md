
# Hotel MANAGEMENT SYSTEM
## FRAMEWORK AND LANGUAGE USED
* JAVA 17
* MAVEN
* SPRINGBOOT 3.1.1
* H2 console
<!-- Headings -->   
## DATA FLOW

<!-- Code Blocks -->

  ### CONTROLLER
  ``` 
package com.geekster.HotelManagement.controller;

import com.geekster.HotelManagement.model.HotelRoom;
import com.geekster.HotelManagement.service.RoomService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class RoomController {

    @Autowired
    RoomService roomService;

    //read
    @GetMapping("rooms")
    public Iterable<HotelRoom> getAllRooms()
    {

        return roomService.getAllRooms();
    }


    @PostMapping("room")
    public String addRoom(@RequestBody HotelRoom room)
    {
        return roomService.addRoom(room);
    }
}
```


 ### MODEL
  #### Hotel Room
  ```
package com.geekster.HotelManagement.model;


import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.Id;
import jakarta.persistence.Table;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@Data
@AllArgsConstructor
@NoArgsConstructor
@Entity
@Table(name = "Room")
public class HotelRoom {
    @Id
    private Long roomId;
    @Column(unique = true)
    private Integer roomNumber;
    private Type roomType;
    private Double roomPrice;
    @Column(name = "status")
    private Boolean roomStatus;
}

```
 #### Type
  ``` 
package com.geekster.HotelManagement.model;

public enum Type {
    AC,
    NON_AC
}
```


### REPO
  ``` 
package com.geekster.HotelManagement.repository;

import com.geekster.HotelManagement.model.HotelRoom;
import org.springframework.data.repository.CrudRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface IRoomRepo extends CrudRepository<HotelRoom,Long> {
}
```


### SERVICE
  ``` 
package com.geekster.HotelManagement.service;

import com.geekster.HotelManagement.model.HotelRoom;
import com.geekster.HotelManagement.repository.IRoomRepo;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class RoomService {

    @Autowired
    IRoomRepo roomRepo;

    public Iterable<HotelRoom> getAllRooms() {
        return roomRepo.findAll();
    }

    public String addRoom(HotelRoom room) {
        roomRepo.save(room);
        return "added";
    }
}

```


### MAIN
  ``` 
package com.geekster.HotelManagement;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HotelManagementApplication {

	public static void main(String[] args) {
		SpringApplication.run(HotelManagementApplication.class, args);
	}

}


```


 ### POM
  ``` 
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.1.1</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.geekster</groupId>
	<artifactId>Hotel-Management</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>Hotel-Management</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<optional>true</optional>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<configuration>
					<excludes>
						<exclude>
							<groupId>org.projectlombok</groupId>
							<artifactId>lombok</artifactId>
						</exclude>
					</excludes>
				</configuration>
			</plugin>
		</plugins>
	</build>

</project>

```
## DATA STRUCTURE USED
* LIST 
* STRING
* LOCAL DATE
* INTEGER
* USER

# PROJECT SUMMARY

## Hotel MANAGEMENT SYSTEM Has been created with the following attribute

* roomId
* roomNumber
* roomType
* Email
* roomPrice
* roomStatus
### Endpoint to be provided 
* AddRoom 
* getroom/{roomid}
* getAllroom
* updateroomInfo
* deleteroom









<!-- Headings -->   
# Author
SHUBHAM PATHAK
 <!-- UL -->
* Twitter <!-- Links -->
[@ShubhamPathak]( https://twitter.com/Shubham15022000)
* Github  <!-- Links -->
[@ShubhamPathak]( https://github.com/ShubhamPatha)
<!-- Headings -->   
