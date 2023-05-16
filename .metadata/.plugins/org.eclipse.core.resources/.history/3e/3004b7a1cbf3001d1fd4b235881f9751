package com.onerivet.deskbook.controllers;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PutMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import com.onerivet.deskbook.models.payload.EmployeeDto;
import com.onerivet.deskbook.models.payload.ProfileViewDto;
import com.onerivet.deskbook.models.payload.UpdateProfileDto;
import com.onerivet.deskbook.models.response.GenericResponse;
import com.onerivet.deskbook.services.EmployeeService;

import jakarta.validation.Valid;


@RestController
@Validated
@RequestMapping("/api/deskbook/user-profile")
public class EmployeeController {

	@Autowired
	private EmployeeService employeeService;

	/**
	 * @purpose: Get all employees
	 * @return: List of employeeDto
	 */
	@GetMapping("/employees")
	public GenericResponse<List<EmployeeDto>> getAll() {
		GenericResponse<List<EmployeeDto>> genericResponse = new GenericResponse<>(this.employeeService.getAllEmployees(), null);
		return genericResponse;
	}

	/**
	 * @purpose: Get employee by id
	 * @param: id
	 * @return: employeeDto
	 */
	@GetMapping("/{id}")
	public GenericResponse<ProfileViewDto> getById(@PathVariable("id") String id) throws Exception {
		GenericResponse<ProfileViewDto> genericResponse = new GenericResponse<>(this.employeeService.getEmployeeById(id), null);
		return genericResponse;
	}
	
	@PutMapping("/{id}")
	public ResponseEntity<GenericResponse<ProfileViewDto>> updateById(@PathVariable("id") String id, @RequestBody @Valid UpdateProfileDto newEmployee)
			throws Exception {
		this.employeeService.updateEmpById(id, newEmployee);
		GenericResponse<ProfileViewDto> genericResponse = new GenericResponse<>(this.employeeService.updateEmpById(id, newEmployee), null);
		return new ResponseEntity<GenericResponse<ProfileViewDto>>(genericResponse, HttpStatus.OK);
	}

}
